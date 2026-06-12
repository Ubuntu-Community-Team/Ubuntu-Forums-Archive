---
title: "massive search and replace of characters in a file"
date: 2006-11-22
forum: General Help
---

### Post by marianom on 2006-11-22
Due a problem in my charset encoding I now have a directory full of text files where certain characters must be replace with others. 
Can anyone suggest what commands or combination of commands I should use from the terminal to seek this directory (and its subdirectories) find all the files where these characters exist and replace them with other desired characters?

As always, thanks a lot.

---

### Post by marianom on 2006-11-22
I find this command might help:

find ./ -name "*.html" -exec sed -i 's/Ã³/ó/g' {}\;

However I still have a problem because when I execute it it says:
missing parameter for '-exec'

Can anyone tell me what I'm missing?

Thanks.

---

### Post by mvaniersel on 2006-11-22
I think you need to quote the {} part, like this:

```

find ./ -name "*.html" -exec sed -i 's/Ã³/ó/g' '{}' \;

```

---

### Post by marianom on 2006-11-22
Cool, it worked, thanks a lot.

If you don't mind a little extra question:

I need to use "&" as a replacement character and it seems it's interpreting it in another way since it does not copy it.

Example:
find ./ -name "*.html" -exec sed -i 's/ó/&oacute;/g' '{}' \;

It does not copy the & making the file imposible to read. I try with the escape character \ but nothing happened. 
Can you tell what I need there to make it copy the ampersand?

Thanks a lot

---

