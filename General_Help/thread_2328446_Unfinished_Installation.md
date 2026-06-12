---
title: "Unfinished Installation"
date: 2016-06-21
forum: General Help
---

### Post by sccjono on 2016-06-21
Hello all,

I have been using Prey ([https://preyproject.com/](https://preyproject.com/)) on my laptop for some time with no issues. However, I recently performed a fresh install of 16.04 and when I came to install the Prey client I seem to have broken it. The application installation appeared to fail at the point where the configuration took place and so I manually configured the app and it seems to be working. However, whenever I perform an 'sudo apt upgrade' I get told that one application is not fully installed or removed. Can anyone please help?

Regards,
jono

---

### Post by yancek on 2016-06-21
What application might that be?

---

### Post by Frogs Hair on 2016-06-21
Prey is available in the 16.04 repository. Did you download the package from the website ?  You could try the following command report any errors. 

```
sudo apt-get -f install
```

---

### Post by ventrical on 2016-06-21
> **sccjono said:**
> Hello all,

I have been using Prey ([https://preyproject.com/](https://preyproject.com/)) on my laptop for some time with no issues. However, I recently performed a fresh install of 16.04 and when I came to install the Prey client I seem to have broken it. The application installation appeared to fail at the point where the configuration took place and so I manually configured the app and it seems to be working. However, whenever I perform an 'sudo apt upgrade' I get told that one application is not fully installed or removed. Can anyone please help?

Regards,
jono

```


sudo dpkg --configure -a

then

sudo dpkg install -f

```

then again

```

sudo apt-get update
sudo apt-get dist-upgrade

```


regards..

---

### Post by sccjono on 2016-06-22
Thank you for the responses but both command give the following error and yes I did install from the website as it is newer than the repository version..

```

Installing init scripts.
dpkg: error processing package prey (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 prey

```

---

### Post by ventrical on 2016-06-22
> **sccjono said:**
> Hello all
However, whenever I perform an 'sudo apt upgrade' I get told that one application is not fully installed or removed. Can anyone please help?

Regards,
jono

Can you tell us what application that is? Could you post the output from the terminal here?

thanks

---

### Post by Geoffrey_Arndt on 2016-06-22
Simple solution . . install from the repo UNLESS it just doesn't meet the must-have functionality you need (versus the "nice to have" functionality).

---

### Post by sccjono on 2016-06-23
See my first post. It is Prey.

I'm not sure how installing from the repo can fix a partially installed package. It just tells me I have a newer version when I try?

So this is a link to the output

[https://www.dropbox.com/s/uiwmgnhzj7ibsew/1.log?dl=0](https://www.dropbox.com/s/uiwmgnhzj7ibsew/1.log?dl=0)

---

### Post by QDR06VV9 on 2016-06-23
This should purge the broken package and conf

 ```
sudo apt-get purge prey
```
let us know.

---

### Post by sccjono on 2016-06-26
Yes that has removed everything thank you. Now I just have to work out why it won't install properly.

Jon

---

### Post by RobGoss on 2016-06-26
Hello Jon have you try installing Prey using **Synaptic Package manager **it might me your best option seeing you're are having trouble installing it,

Updated

---

### Post by howefield on 2016-06-26
> **RobGoss said:**
> ... it just make sure you enable **Canonical partners (source code ), **from **Software & updates **section.

Why would the OP do that ?

---

### Post by RobGoss on 2016-06-26
> **howefield said:**
> Why would the OP do that ?

I was under the impression when using **Synaptic package manager **and installing apps we need to **enable Canonical partners** [COLOR=#000000]is this not correct?[/COLOR]

---

### Post by QLee on 2016-06-26
> **RobGoss said:**
> I was under the impression when using **Synaptic package manager **and installing apps we need to **enable Canonical partners** [COLOR=#000000]is this not correct?[/COLOR]

Only if one needs something from the partners repository, the application that the OP is asking about, prey, is in universe.

---

### Post by RobGoss on 2016-06-26
> **QLee said:**
> Only if one needs something from the partners repository, the application that the OP is asking about, prey, is in universe.

Oh I see so he would still be able to install prey using **Synaptic package manager ****correct**

---

### Post by howefield on 2016-06-26
> **RobGoss said:**
> Oh I see so he would still be able to install prey using **Synaptic package manager ****correct**

Yes, with the Universe repository loaded, correct.

---

