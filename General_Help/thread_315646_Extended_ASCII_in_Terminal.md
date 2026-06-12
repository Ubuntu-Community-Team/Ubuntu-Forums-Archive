---
title: "Extended ASCII in Terminal?"
date: 2006-12-09
forum: General Help
---

### Post by kewldude606 on 2006-12-09
Is there anyway to get extended ASCII support in the Terminal (the high numbers like 191, etc.)?  I have the character encoding in the Terminal set to UTF-8 which, from what I gather on wikipedia, is backwards compatible with ASCII.

When I run this anything that outputs a high ASCII char, a blackdiamond with a question mark inside is displayed to the terminal.

Is there anyway around this?

Thanks,
Dan

---

### Post by szigetva on 2007-01-07
You should set encoding to the appropriate one-byte encoding (like iso-8859-n, where n is one for Western Europe, 2 for Eastern Europe etc.).

---

### Post by MasterZ on 2007-02-10
Hello, 

I have the same problem, I'm getting the contents of a web page with cURL and when it's displayed in the terminal, the accents are replaced by black diamonds with question mark. 

If I manually change the character encoding of the terminal to ISO-8859-2, I can view the output normally. 

However I use this line in a bash script and I do not know how to make the environment in which the script runs compatible with ISO-8859-2. 

I checked the locale in gnome-terminal before and after changing the character encoding, but the locale are the same. So I don't know what to set in my bash script. 

Does anyone know how to do this ?

Thanks,

MasterZ

---

