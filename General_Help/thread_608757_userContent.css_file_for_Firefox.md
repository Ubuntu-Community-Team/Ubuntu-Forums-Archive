---
title: "userContent.css file for Firefox"
date: 2007-11-10
forum: General Help
---

### Post by liquidcross on 2007-11-10
I'm trying to install a custom userContent.css file into Firefox to block ads. I've tried the solution listed [here]("http://ubuntuforums.org/showthread.php?t=469650"), but it didn't work. I get a "file not found" error. I even tried copying my userContent.css file to /etc/firefox/profile/chrome, and that didn't work either. What's really strange is that while the file is visible in the folder if I open it, the file does *not* show up in search results, as if it doesn't exist! 

Any thoughts?

---

### Post by liquidcross on 2007-11-13
*bump*

---

### Post by tbzep on 2008-01-11
> **liquidcross said:**
> I'm trying to install a custom userContent.css file into Firefox to block ads. I've tried the solution listed [here]("http://ubuntuforums.org/showthread.php?t=469650"), but it didn't work. I get a "file not found" error. I even tried copying my userContent.css file to /etc/firefox/profile/chrome, and that didn't work either. What's really strange is that while the file is visible in the folder if I open it, the file does *not* show up in search results, as if it doesn't exist! 

Any thoughts?

I'm not sure if you mean you just can't find the correct location or if your userContent.css file just didn't work, so I may be way off base here.

My userContent.css file goes in this folder:

/[your username]/.mozilla/firefox/[randomly generated number.default]/chrome

"randomly generated number.default" will have random characters similar to  "xyz123xy.default".  Mine has sample userContent-example.css and userChrome-example.css files sitting in the folder, but there was no actual userContent.css file until I created one there.

I just now fixed my NASA theme to show the shuttle launch on new tabs all the time with the userContent.css file.  

BTW, you can use this to locate files in the terminal also.

```
locate userContent.css
```

---

