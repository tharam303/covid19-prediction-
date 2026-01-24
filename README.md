import pandas as pd

data = {
    "Date": [
        "2020-03-01","2020-03-02","2020-03-03","2020-03-04","2020-03-05",
        "2020-03-06","2020-03-07","2020-03-08","2020-03-09","2020-03-10"
    ],
    "Country": ["India"] * 10,
    "State": [
        "Tamil Nadu","Kerala","Karnataka","Maharashtra","Delhi",
        "Tamil Nadu","Kerala","Karnataka","Maharashtra","Delhi"
    ],
    "Confirmed": [120,150,180,230,300,360,420,500,600,750],
    "Deaths": [2,3,4,6,8,10,12,15,20,25],
    "Recovered": [10,18,25,40,60,90,130,180,250,350]
}

df = pd.DataFrame(data)

df["Active"] = df["Confirmed"] - df["Deaths"] - df["Recovered"]
df["Daily_New_Cases"] = df["Confirmed"].diff().fillna(0)
df["Mortality_Rate"] = (df["Deaths"] / df["Confirmed"]) * 100
df["Recovery_Rate"] = (df["Recovered"] / df["Confirmed"]) * 100

print(df)
