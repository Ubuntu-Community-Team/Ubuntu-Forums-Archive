---
title: "Help With PidginTex (pidgin addon)"
date: 2008-07-04
forum: General Help
---

### Post by dethredic on 2008-07-04
Ok, so I have been trying to get this plugin to work.
The main site is [here]("http://code.google.com/p/pidgintex/")

I have installed the plugin fine, and it works, but what is not working is the mimeTex/ mathTex. I followed the instructions found [here]("http://code.google.com/p/pidgintex/wiki/mimeTeXmathTeXHowto")and installed them without error.

I now try and use it and I enter: $$ sqrt (4+5/2) $$ this gives me an error that it could not find mimtex. I change the value to mathtex and I get the same error.

Now I go to the Windows Installation page (I didn't see a Linux one). It says  you need to modify the .bat with the path to mimtex/mathtex. I have not done that which is probably why I was getting the errors. The only problem is that afaik .bat files are for windows (dos pretty much) and not for Linux. So I could not find information anywhere on how to specify where mathtex/mimetex are installed.

Any ideas?

---

### Post by dethredic on 2008-07-05
anyideas?

---

### Post by prshah on 2008-07-05
> **dethredic said:**
> 
So I could not find information anywhere on how to specify where mathtex/mimetex are installed.


use the commands ```
sudo updatedb
sudo locate -i mathtex

``` to find out where the extensions are located; then, add them to your path with ```
export PATH=$PATH:/path/to/mathtex
``` Don't include the filename in the path!

And then check if it is activated in Pidgin.

---

