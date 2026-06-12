---
title: "Save password for URL pattern in Firefox?"
date: 2007-08-05
forum: General Help
---

### Post by ThinkBuntu on 2007-08-05
The IT people at my University think themselves very clever. When you go to the email login URL, (say, [http://webmail.foo.edu/](http://webmail.foo.edu/)) a random number is affixed to the end of the URL ([http://webmail.foo.edu/12344151](http://webmail.foo.edu/12344151)) making password saving, as far as I know, impossible. Is there a way I can have Firefox save my password, which is prompted by what appears to be a JavaScript alert dialog, for all instances of the base URL? Firefox does give me the "Save Password" option, but it's useless when that number is different every time.

---

### Post by apswartz on 2007-08-05
May not work, but worth a try...
examine the html source to see what the variable names are, e.g., **username** and **password**
then edit your bookmark as...
```
http://webmail.foo.edu?username=yourusername&password=yourpassword
```

Another possibility is to use the **Autofill Form** extension...
[https://addons.mozilla.org/en-US/firefox/addon/4775](https://addons.mozilla.org/en-US/firefox/addon/4775)

---

