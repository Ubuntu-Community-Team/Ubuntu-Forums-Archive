---
title: "add remove question"
date: 2008-02-25
forum: General Help
---

### Post by puppetj on 2008-02-25
I know about add/remove in ubuntu and apt-get, tum, snypatic p manager, but is there gui app that i can install that remove anything thats installed by anymeans, like if i install a deb or a rpm app??
b/c those that are install do not show up in those "add/remove" apps..also, i really want to get cnr running, i know its in beta, but i installed it both ways as it gave me the steps to, and i can get it to run or work.

---

### Post by Bubba64 on 2008-02-26
As far as I know the only thing in add remove is whats already there depending on if you have the drop down everything available or any of the other four options. I believe anything you install or down load goes into synaptic, the key is knowing what to put in the search bar to look for it. I am not an expert on this though so look for more sound information. The terminal function if you know how to use it can find programs as well.

---

### Post by puppetj on 2008-02-26
parkay thanks,,,

---

### Post by Yellow Pasque on 2008-02-26
```
sudo apt-get install aptitude
sudo aptitude
```
:)

---

### Post by S3Indiana on 2008-02-26
> **puppetj said:**
> ..also, i really want to get cnr running, i know its in beta, but i installed it both ways as it gave me the steps to, and i can get it to run or work.What error message do you get when unsuccessfully installing the CNR [Client]("http://www.cnr.com/supportPages/aboutDownloadPlugin.seam")???

---

### Post by puppetj on 2008-02-26
[S3Indiana]


I get no error message after installing the cnr the 1st way you can, it even shows up in the system tool menu, but when i click on it it doesnt run, and when i goto cnr.com, and install something nothing happens, so i even followed the 2nd way to install by terminal, and it doesnt even see it in the apt-get  to install.. but i can remove the 1st install with apt-get... 

[Temüjin]  

 whats aptitude???

---

### Post by S3Indiana on 2008-02-26
> **puppetj said:**
> [S3Indiana]

I get no error message after installing the cnr the 1st way you can, it even shows up in the system tool menu, but when i click on it it doesnt run, and when i goto cnr.com, and install something nothing happens, so i even followed the 2nd way to install by terminal, and it doesnt even see it in the apt-get  to install.. but i can remove the 1st install with apt-get... Pls. run cnr from the command prompt and reply with any error messaging...

---

### Post by puppetj on 2008-02-27
i get:

"package cnr-client is not available, but is referred to another package
this may mean that the package is missing 
E: package cnr-client has no install candidate 

that's what i get

---

### Post by S3Indiana on 2008-02-27
> **puppetj said:**
> i get:

"package cnr-client is not available, but is referred to another package
this may mean that the package is missing 
E: package cnr-client has no install candidate 

that's what i getPls run from the command prompt: apt-cache policy cnr-client
```
cnr-client:
  Installed: 0.2.3xxx
  Candidate: 0.2.3xxx
```
Don't think the CNR Client is installed properly...

---

### Post by puppetj on 2008-02-27
yes i know, thats what iam trying to do get it installed, but i just get that error

as for typing that i get no versiom installed on both lines, b/c it not installed

apt-get install cnr-client freespire-blah blah is suppose to install it.

---

### Post by S3Indiana on 2008-02-27
> **puppetj said:**
> yes i know, thats what iam trying to do get it installed, but i just get that error

as for typing that i get no versiom installed on both lines, b/c it not installed

apt-get install cnr-client freespire-blah blah is suppose to install it.Sorry. The easiest install probably is using the CNR Client [download]("http://www.cnr.com/supportPages/aboutDownloadPlugin.seam") link for your version, but if apt is desired pls. visit [here]("http://community.cnr.com/docs/DOC-1035") (to update your sources)...

---

### Post by puppetj on 2008-02-27
np, but like i mentioned ..sigh.. that it doesnt work either..just read..

yes i know about that, i follow the those steps in the "terminal" install, when the other didnt work

---

### Post by S3Indiana on 2008-03-13
> **puppetj said:**
> np, but like i mentioned ..sigh.. that it doesnt work either..just read..

yes i know about that, i follow the those steps in the "terminal" install, when the other didnt workAn [updated]("http://www.cnr.com/supportPages/aboutDownloadPlugin.seam") version of the CNR Client has been released that quite possibly could resolve your issues...

---

### Post by puppetj on 2008-03-21
thanks, it did work in a new install ubuntu on another pc, dunno about the other install because its gone, but i think it might of but i think it was a bad install of ubuntu, in the 1st place, b/c i ran into other issues, like it not installing grub, and stuff, thanks you letting me know, i hope that this will become as big as steam :) got any good suggestions on things on cnr to check out any categorie is fine.

---

### Post by S3Indiana on 2008-03-21
> **puppetj said:**
> i hope that this will become as big as steam :) got any good suggestions on things on cnr to check out any categorie is fine.Depending what you're looking for an updated [amaroK]("http://cnr.com/product/productOverview.seam?productId=18250") (1.4.8 ) is available, latest [Google Earth]("http://cnr.com/product/productOverview.seam?productId=16206") (4.2), [Firefox 3]("http://cnr.com/product/productOverview.seam?productId=37376") beta (3.0 b3 for 7.10 soon to be b4),  [skype]("http://cnr.com/product/productOverview.seam?productId=17937") beta (2.0) w/ video capability for starters. More soon to come.

---

