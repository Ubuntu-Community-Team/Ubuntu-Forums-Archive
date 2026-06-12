---
title: "Dansguardian filtering help"
date: 2006-10-09
forum: General Help
---

### Post by eg-maverick on 2006-10-09
How do you adjust the filtering controls in Dansguardian? I am getting blocked from getting to things like Yahoo!groups, yahooDSL, etc. The warning is:
Access to the page has been denied.

URL: [http://groups.yahoo.com/](http://groups.yahoo.com/)
ICRA chat PICS labeling level exceeded on the above site.

Access to the page has been denied.

URL: [http://www.sbc.com/gen/general?pid=6431](http://www.sbc.com/gen/general?pid=6431)
Weighted phrase limit exceeded.

---

### Post by tonhou on 2006-10-09
Here is documentation from DG website:

[http://dansguardian.org/downloads/detailedinstallation2.html#further](http://dansguardian.org/downloads/detailedinstallation2.html#further)

which explains various configuration files.

--Tony

---

### Post by eg-maverick on 2006-10-18
> **tonhou said:**
> Here is documentation from DG website:

[http://dansguardian.org/downloads/detailedinstallation2.html#further](http://dansguardian.org/downloads/detailedinstallation2.html#further)

which explains various configuration files.

--Tony

Tony,
I appreciate the pointer. The problem I am having is I read all the info on the config files and can'ge seem to make a tweek that works. Like I said, I don't know of any special "trigger" word that will pop up when I am trying to get to yahoo groups home page. I set the bias for chat to allow some but that didn't change the behavior. Likewise, on the nutrition page, I can't find anything offensive on it so I don't know what to adjust. Any other help?
Craig

---

### Post by tonhou on 2006-10-18
On the page referred to above it mentions the "exceptionsitelist" file found in /etc/dansguardian.

If you put sites in there that you don't want blocked then they won't be!

--Tony

---

### Post by stilus on 2006-11-30
A little detail that might help: you need to restart/ reload dansguardian for the new settings/ grouplists etc to work. On debian (an old one, but with DG 2.9.x) I found the "reload" part quoted out in /etc/init.d/dansguardian. 
I just removed the quotes, and I had **/etc/init.d/dansguardian** reload functionality.

I guess (guess being the important word here) its Dansguardians architecture to need a reload for new groupsettings etc. to take effect... If anyone can tell me otherwise (and how to go about it) I'd be much obliged!

I forgot: there is something called "naughtyness level" or something to that effect in the configuration files. You might want to tweak that up a little too

---

