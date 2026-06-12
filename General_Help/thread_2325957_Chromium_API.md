---
title: "Chromium API"
date: 2016-05-26
forum: General Help
---

### Post by BJones007 on 2016-05-26
I found myself trying to add API's for Chromium, but I've encountered a problem that I'm not sure how to wrap my head around. This all started cos I wanted to watch Netflix, but apparently those plugins aren't available in Chromium. Anyway, I found this article titled API Keys [here]("http://www.chromium.org/developers/how-tos/api-keys"). I did everything up to the point where it says "Providing Keys at Build TIme", but I'm unable to find or create the file called .gyp as it either doesn't exist or I dunno how to find it.

I ran this command ```
 sudo gksudo gedit ~/.gyp/include.gypi 
``` and it brought me to a blank page for me to edit and add the keys using this command
```
 [COLOR=#000000][FONT=&amp]**{**[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**  'variables': {**[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**[SIZE=2]    'google_api_key':               '*your_api_key*[/SIZE]**[/FONT][/COLOR][COLOR=#000000][FONT=&amp][SIZE=2]',[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    'google_default_client_id':     '*your_client_id*[/FONT][/COLOR][COLOR=#000000][FONT=&amp]',[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][SIZE=2]    'google_default_client_secret': '*your_client_secret*[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial][FONT=&amp][SIZE=2]',[/SIZE][/FONT][/FONT][/COLOR]
[FONT=courier new][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=&amp]    # … other variables you may have ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  },[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]}[/FONT][/COLOR]
``` 

Pretty simple right? Wrong. When I tried to save the document I got this error

> 
Could not find the file “/root/.gyp/include.gypi”.

 I'm having an issue with the stable version of Google Chrome as it keeps crashing and that's the main reason I switched over to Chromium. Now I'm not sure how to continue. Please help :(

---

### Post by vasa1 on 2016-05-26
That link indicates, at least to me, that not anyone can acquire API keys. Apparently, you need to get some sort of authorization.

Without knowing more, I'm guessing it would be easier to fix whatever's wrong with Google Chrome.

---

### Post by BJones007 on 2016-05-26
> **vasa1 said:**
> That link indicates, at least to me, that not anyone can acquire API keys. Apparently, you need to get some sort of authorization.

Without knowing more, I'm guessing it would be easier to fix whatever's wrong with Google Chrome.


I've already acquired the keys for both API and OAuth, but it's just that one little step that is throwing me off. 


In regards to Google Chrome I'm not sure how to go about fixing it cos as soon as I launch it and try to open a webpage it freezes, goes dark, then crashes. Then the error report window shows up. Tried removing and re-installing it, but no dice.

---

### Post by BJones007 on 2016-05-27
Bump

---

