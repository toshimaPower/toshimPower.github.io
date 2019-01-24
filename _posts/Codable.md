
# Codable Memo

## Codable オブジェクトをほぼ同じの別の Codable ObjectにCopy  

今のところの私のアイディア  
長い、短くしたいが頭が悪くて、、、、

順
* Codable ObjectをEncodableでJsonを作る
* JsonをJSONSerializationでdataを生成
* dataを別のObjectにDecode

```swift  
  let encoder = JSONEncoder()
  encoder.keyEncodingStrategy = keyEncodingStrategy
  let encoded = try encoder.encode(self)
  
  let jsonobject = try JSONSerialization.jsonObject(with: encoded, options: JSONSerialization.ReadingOptions.allowFragments)
  
  let jsondata: Data = try? JSONSerialization.data(withJSONObject: jsonobject, options: JSONSerialization.WritingOptions.prettyPrinted)
  try JSONDecoder().decode(Codable.self, from: jsondata)
  
```

