# HarmonicaPatchExample
Пример манифеста для патчера Harmonica

Пожалуй, стоит рассказать в целом про функционал. С помощью Harmonica вы можете создавать и рапространять так называемые патчи - архивы с набором файлов .patch используемые для дальнейшей статической модификации приложения Max (ru.oneme.app). Про файлы .patch и diff можно почитать [по ссылке](https://www.freecodecamp.org/news/git-diff-and-patch/). Чтобы Harmonica разпознала ваш патч вам необходимо предоставить манифест. Что же он из себя представляет?

Вот манифеста патча:
```xml
<harmonica>
  <version>1</version>
  <patch-info>
    <title>Мой супер крутой патч!</title>
    <description>Мой патч добавляет аниме-девочку сусейку десу~</description>
    <patchable-version>26.8.0 (6596)</patchable-version>
    <frida>false</frida>
    <frida-version></frida-version>
    <update-url>https://github.com/...</update-url>
    <author>nyakaii</author>
  </patch-info>
</harmonica>
```
Теперь же давайте ПОМИНУТНО разберем что где писать?

## Harmonica Manifest
`<harmonica>` - корень. Обязательная часть

`<version>` - версия манифеста. Ставьте всегда 1
### Patch Info
`title` - Название вашего патча. String

`description` - Описание вашего патча. String

`patchable-version` - Конкретная версия (versionCode). String

`frida` - Нужно ли инжектить [frida](https://frida.re)? 

Важно заметить, что сначала рассматривается frida и если данная опция включена, то `update-url` необязателен. В таком случае ссылку на скрипт необходимо указать в `frida-url`. Boolean

`frida-version` - Версия frida, которую необходимо инжектнуть. При отсутствии версии скачается последняя. Ни на что не влияет при отключенном `frida`. String

`frida-url` - Ссылка откуда необходимо скачать скрипт для frida. Ни на что не влияет при отключенном `frida`. String

`update-url` - Ссылка на архив, откуда необходимо скачать набор патчей. String

`author` - Автор патча. String
