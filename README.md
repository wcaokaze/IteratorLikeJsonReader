
IteratorLikeJsonReader
================================================================================

特にメリットはないので[kotlinx.serialization](https://github.com/Kotlin/kotlinx.serialization)
などを使った方がいいです。

JSONをIterator風に読み込むためのライブラリです。

```java
long id = -1L;
String username = null;

try (final IteratorLikeJsonReader jsonReader = new IteratorLikeJsonReader(inputStream)) {
   try {
      jsonReader.openObject();

      String key;
      while ((key = jsonReader.nextKey()) != null) {
         switch (key) {
            case "id":
               id = jsonReader.readLong();
               break;
            case "username":
               username = jsonReader.readString();
               break;
         }
      }
   } finally {
      jsonReader.closeObject();
   }
}

return new User(id, username);
```

