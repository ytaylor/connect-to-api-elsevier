# connect-to-api-elsevier
In this example show how to connect with the API ElSevier and retrieve information about citations to academic papers. 

## Connect to Google Drive
The database of citation to find are excel file in Goole Drive, so the first step is connect to Google Drive an obtain the file with data. 

```
from google.colab import drive, auth
drive.mount('/content/gdrive')
GDRIVE_BASE_DIR = 'path_to_data:information'
print(GDRIVE_BASE_DIR)

sh = gc.open('name_wb')
wh = sh.worksheet("name_wh")
```

## Connect to API ElSevier

To connect to API ELSevier is necesary preview have a API Key and save in a json file with a name config.json

```
{
    "apikey": "XXXXXXXXXXXXXXXXXXXXXXXX"
}
```
Then is posible 

```
import requests
import json
    
## Load configuration
con_file = open(GDRIVE_BASE_DIR+"config.json")
config = json.load(con_file)
con_file.close()


## Find information empty fields citations
citations_wh = sh.worksheet('citations')
citations_rows = citations_wh.get_all_values()
citations_df = pd.DataFrame.from_records(citations_rows[1:], columns=citations_rows[0])

```

## Rerieve Information 

