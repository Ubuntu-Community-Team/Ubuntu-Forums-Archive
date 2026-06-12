---
title: "Terminal error bashrc syntax error unexpected end of file"
date: 2014-03-20
forum: General Help
---

### Post by Luxx on 2014-03-20
bash: /home/v/.bashrc: line 129: syntax error: unexpected end of file

This shows at the top of my terminal every time I open it. Things usually work fine in terminal, but I'm wondering what is going on with this message at the top. Interestly, there is no line 129 as .bashrc ends at line 128, although I'm not sure that should be unexpected. I haven't made any deliberate changes to it. Any ideas why I get this message at the top of my terminal or how to make it go away?

---

### Post by steeldriver on 2014-03-20
Maybe there's a missing newline or some control characters that you're not seeing? try

```

cat -An ~/.bashrc | tail -3

```

to see the last few lines with control characters / line endings

---

### Post by Impavidus on 2014-03-21
bash tries to read line 129, sees that there is no line 129 and then gives an error message. My guess is a missing quote somewhere in your .bashrc file.

---

### Post by Luxx on 2015-01-06
Sorry guys, I was out of commission for a while... but my issue was eventually solved with the fix found here:
[http://askubuntu.com/questions/521398/bash-error-on-opening-the-terminal](http://askubuntu.com/questions/521398/bash-error-on-opening-the-terminal)

```
cp /etc/skel/.bashrc ~
```

Just in case anyone with a weird message at the top of their terminal emulator comes across this thread while searching.
Keep in mind I don't have a lot going on in my .bashrc file anyway. Be sure to make a backup just in case.
Thanks.

ps - This also got rid of a later error:

"Unknown ruby interpreter version (do not know how to handle): textmate. Could not load ruby textmate."

---

