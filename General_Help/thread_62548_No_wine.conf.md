---
title: "No wine.conf ?"
date: 2005-09-05
forum: General Help
---

### Post by muzzie on 2005-09-05
Well, I installed Wine alright, and it does indeed run, but I am looking for the wine.conf file referenced all over the place in guides and such.
I looked in the ~./wine/config directory and nothing is there.  In fact, there is no /config directory at all.
There is supposed to be a sample wine.conf file in the /documentation/samples directory of the Wine source code directory, but I can't find one there either (downloaded the source just to try and find that...).

Any ideas? Perhaps someone with the appropriate conf file can upload it for me?
Puzzling why I don't have one.

---

### Post by arnieboy on 2005-09-05
[QUOTE=muzzie]Well, I installed Wine alright, and it does indeed run, but I am looking for the wine.conf file referenced all over the place in guides and such.
I looked in the ~./wine/config directory and nothing is there.  In fact, there is no /config directory at all.
There is supposed to be a sample wine.conf file in the /documentation/samples directory of the Wine source code directory, but I can't find one there either (downloaded the source just to try and find that...).

Any ideas? Perhaps someone with the appropriate conf file can upload it for me?
Puzzling why I don't have one.[/QUOTE]
u are possibly looking for ~/.wine/config
if u dont have one, use mine. 
refer to [http://frankscorner.org](http://frankscorner.org) for more help in setting up wine.
remember to rename the attachment as config (from config.txt before u use it)

---

### Post by muzzie on 2005-09-05
[QUOTE=arnieboy]u are possibly looking for ~/.wine/config
if u dont have one, use mine. 
refer to [http://frankscorner.org](http://frankscorner.org) for more help in setting up wine.
remember to rename the attachment as config (from config.txt before u use it)[/QUOTE]
Yes, that's what I meant.  Typoed the path in my post :D

Thanks a bunch!

---

### Post by wadesmart on 2005-09-05
09052005 1521 GMT-5

I didnt have a config file either. I did a search for config and finally found it in a odd location. I did a full system search. 

wade

---

### Post by muzzie on 2005-09-05
Well, I just got an email from Frank Hendriksen (runs the website "Frank's Corner" for configuring Wine apps - [www.frankscorner.org](www.frankscorner.org) )

Here is what he said-
> 
Since the 20050628 version Wine doesn't use the config file anymore. All
the configuration has gone to Wine's registry (system.reg and user.reg)

You can now use the utility "winecfg" to configure Wine, though it does seem to be lacking the depth a pure config text file would have.

---

### Post by davidr on 2005-10-11
And.....?
If we want to manage our wine with de wone.conf file, how to downgrade?. The new system drives me crazyyyyyyy!!!!
SNORT!!!!
NARF!!!!!

---

### Post by jamesstansell on 2005-10-11
[QUOTE=davidr]And.....?
If we want to manage our wine with de wone.conf file, how to downgrade?. The new system drives me crazyyyyyyy!!!![/QUOTE]

If you don't want to use winecfg, just edit the .wine/*.reg files with a text editor.

---

