---
title: "Downgrading to Firefox 1.5 in Edgy?"
date: 2006-10-30
forum: General Help
---

### Post by Epperly on 2006-10-30
Is there a repo you can change or anything to get 1.5 in Edgy.. that is the only reason I don't want 6.10 because of the crashes I got many many times in Firefox 2, very annoying.

Other than that upgrading again wouldn't be a bother.

---

### Post by dr.drake on 2006-10-31
yes please help:

in firefox2.0 my fonts are still buggy and the "Tab Mix Plus" extension doesn't work and I really miss my "One Window Mode"..

so how do we downgrade to firefox1.5.0.7 ???

---

### Post by dr.drake on 2006-10-31
Wow! I actually thought of a way that worked...

went into synaptic, did a comple uninstall of firefox.
replaced the /etc/apt/sources.list with my old dapper list
sudo apt-get update
installed firefox (console or synaptic)
replaced the sources list with the old new one.

and it works!!!!!
even flash is synced without any additional tweaking now..
all my extensions are installable again...

---

### Post by David Corrales on 2006-10-31
Be sure to lockdown the firefox version inside synaptic, so you don't accidentaly upgrade it back :)

---

### Post by dr.drake on 2006-10-31
;) done    (thanks)

---

### Post by Sethro on 2006-10-31
Yeah I would really like to uninstall Firefox 2.0 and go back to 1.5 


Can anyone make a how to on this 




Thanks

---

### Post by Epperly on 2006-10-31
what are the old sources? can I have them to do the same, then how do I edit to keep it from upgrading? Thanks!

---

### Post by dr.drake on 2006-11-01
kindof a howto: there might be an easier way, but I'm too sleepy to think..
(and I used the edgy souces list from [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories"))

***- make sure you don't have firefox running!!***

open **Synaptic**, search for **firefox**, click box, choose **mark for complete removal**, click **Apply**, close Synaptic.
open a Terminal and type:
```
sudo gedit /etc/apt/sources.list
```
[COLOR="Red"]replace in the following lines the words "**edgy-updates**" with the word "**dapper**" and then safe list:[/COLOR]
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **edgy-updates** main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) **edgy-updates** main restricted universe multiverse
in terminal type:

```
sudo apt-get update
sudo apt-get install firefox
```
in the still open sources.list replace **dapper** with **edgy** again, safe and exit
in terminal type:

```
sudo apt-get update
```
close terminal
open Synaptic and search for firefox, it should now read version 1.5
select **firefox**, click **Package**, select **Lock Version**

done

---

### Post by Epperly on 2006-11-01
You can't replace edgy with dapper it doesn't seem to work that simply
nevermind I got it to downgrade but how do I lock it?

---

### Post by dr.drake on 2006-11-01
> **Epperly said:**
> You can't replace edgy with dapper it doesn't seem to work that simply
nevermind I got it to downgrade but how do I lock it?

fixed in my previous post in red..

thanks

---

### Post by Epperly on 2006-11-01
how do I lock it?

---

### Post by dr.drake on 2006-11-01
> **Epperly said:**
> how do I lock it?
it was in my original post:

> **dr.drake said:**
> 

open Synaptic and search for firefox, it should now read version 1.5
select **firefox**, click **Package**, select **Lock Version**

done

---

### Post by Tobster on 2006-11-01
I have not had any crashes and I love the spell check in the new upgraded fire fox.

The crashes could be due to an hardware problem for me I had no worries and I am over whelm with Edgy.  I just love it so very much

---

