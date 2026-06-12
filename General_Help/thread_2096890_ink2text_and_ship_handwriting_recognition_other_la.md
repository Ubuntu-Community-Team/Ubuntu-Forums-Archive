---
title: "ink2text and ship handwriting recognition other language special characters"
date: 2012-12-21
forum: General Help
---

### Post by davidvandoren on 2012-12-21
Hi there !
I successfully installed the ink2text input panel .
For English everything is working great.
However, when changing the language setup in wine to (German) or Chinese , the input Panel does not display special characters.
It obviously recognizes German but displays a ? for every Umlaut .
The Chinese characters are recognized also but only ? are displayed.
I tried to change the fond in the ship. properties file, but to no avail.

Any Ideas ?
Somehow ship needs to use the proper fond, but I can't figure out which file to edit.
thanks for Your help.

---

### Post by Rexilion on 2012-12-21
I'm just guessing here, so there goes: Do you have 'xfonts-intl-chinese' installed?

---

### Post by davidvandoren on 2012-12-21
> **Rexilion said:**
> I'm just guessing here, so there goes: Do you have 'xfonts-intl-chinese' installed?

Thank's for the reply.

I have just installed the fond then opened the terminal and entered 

```
export LC_MESSAGES=zh_TW.utf8
```

then in the same terminal
```
sh -c "/usr/local/bin/ship/ship & wine /usr/local/bin/RecognitionServer.exe 8888"
```
but no luck

---

### Post by Rexilion on 2012-12-22
Ah, you might have mentioned before that you did not start your session as default zh_TW locale. I incorrecly assumed that, sorry for that.

Try this:

```
export LC_ALL=zh_TW.utf8
export LANG=zh_TW.utf8
sh -c "/usr/local/bin/ship/ship & wine /usr/local/bin/RecognitionServer.exe 8888"
```

---

### Post by davidvandoren on 2012-12-22
> **Rexilion said:**
> Ah, you might have mentioned before that you did not start your session as default zh_TW locale. I incorrecly assumed that, sorry for that.

Try this:

```
export LC_ALL=zh_TW.utf8
export LANG=zh_TW.utf8
sh -c "/usr/local/bin/ship/ship & wine /usr/local/bin/RecognitionServer.exe 8888"
```

Thanks but still no luck.

I think ship never was programmed to recognize any other languages than English. 
The language recognition obviously changes though. When setting it  to German it will write all German words except for the special characters there will be a question mark. 
When I set it to Chinese the red and green outlining definitely show that Chinese is recognised and English word will be recognised as question marks also. 

If anyone knows which file to temper with let me know.

---

### Post by Rexilion on 2012-12-22
Why not install an Ubuntu with that locale as a system default? Who knows what the installer might pull/do to get things working. I know it's a long/tedious shot. But then you will at least know wheather is really does not work or if it's a config issue.

---

### Post by davidvandoren on 2012-12-22
> **Rexilion said:**
> Why not install an Ubuntu with that locale as a system default? Who knows what the installer might pull/do to get things working. I know it's a long/tedious shot. But then you will at least know wheather is really does not work or if it's a config issue.
I already did that in virtualbox for German and Chinese.

It's the same thing.

---

