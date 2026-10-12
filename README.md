# papi
##방송대 저장소
import requests
import pandas as pd

key="088e41f9f9d68394165319dc7309b494f96d4b90571e0757c05dae71c06a1c5d"
category={"01":봄배추","02":"여름배추(고랭지)",
"03":"가을배추","06":"월동배추"}
data=[]

for year in range(2015,2025)
for code, name in category.item():
url=(f"https://apis.data.go.kr/B552845/perDay/price?"
f"servicekey={KEY}&pageNo=1&numOfRows=200&returnType=JSON"
f"&cond[exmn_ymd::GTE]={yaer}0101"
f"&cond[exmn_ymd:GTE]{year}1231"
"&cond[se_cd::EQ]=02&cond[ctgry_cd::EQ]=200"
"&cond[item_cd:EQ]=211&cond[grd_cd::EQ]=04"
"&cond[sgg_cd::EQ]1101&cond[mrkt_cd::EQ]=0110211"
f"&cond[vrty_cd::EQ]{code}")

"color:#6a9955"># API호출
response=requests.get(url)
result=response.json()

"color:#6a9955">#API호출여부 성공 여부 확인(header에서 결과코드와 결과 메세지 추출)
header=result["response"]["header"]
result_cord=header["resultCode"]
result_msg=header["resultMsg"]

print(f"{yaer}년 {name}:")
print(f" response.status_code={response.status_code}")
print(f" resultCode={result_code}")
print(f" resultMsg={result_msg}")
print(str(result["response"]['body']['totalCount'])+"건"

"color:#6a9955"># 호출 성공시 데이터 수집
if response.status_code ==200:
items=result["response"]["body"].get("items",{}).get(item",[])
for x in items:
x["연도"],x["품종"]=yaer,name
data +=items

