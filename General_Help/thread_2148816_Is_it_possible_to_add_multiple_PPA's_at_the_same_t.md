---
title: "Is it possible to add multiple PPA's at the same time?"
date: 2013-05-26
forum: General Help
---

### Post by DaveBaxter on 2013-05-26
Hi, as I like to tinker with my Ubuntu setup (often re-installing etc) I have built up a text file of all the programs that I use the most.

I was just wondering if it is possible to combine the following into a single terminal command to save time as more gets added to the list.;)
```

sudo apt-add-repository ppa:cdemu/ppa
sudo apt-add-repository ppa:fengestad/devel
sudo apt-add-repository ppa:tualatrix/ppa
sudo apt-add-repository ppa:stebbins/handbrake-releases
sudo apt-add-repository ppa:cairo-dock-team/ppa

```
I know I could write a script to add the PPA's but I would prefer a simple one line terminal command if possible.

Thanks.

---

### Post by Dennis N on 2013-05-26
Try joining with && . Does it work? These are interactive. Once this is written, how many times could it be used?

---

### Post by DaveBaxter on 2013-05-27
> **Dennis N said:**
> Try joining with && . Does it work? These are interactive. Once this is written, how many times could it be used?
Hi, && doesn't work, only the first PPA gets added, the rest dont.

Thanks anyway :D

---

### Post by sandyd on 2013-05-27
Now this is a... bit dangerous since you dont get prompts.
```

sudo apt-add-repository -y ppa:cdemu/ppa && sudo apt-add-repository -y ppa:fengestad/devel && sudo apt-add-repository -y ppa:tualatrix/ppa && sudo apt-add-repository -y ppa:stebbins/handbrake-releases && sudo apt-add-repository -y ppa:cairo-dock-team/ppa

```

Also, many flags/operations avlaliable for command-line problems can be determined by running
```

*command* --help
```
or if you want the long version.
```

man command
```

---

### Post by HiImTye on 2013-05-27
```
while read -r r; do sudo apt-add-repository $r; done< <(echo -e 'ppa:cdemu/ppa\nppa:fengestad/devel\nppa:tualatrix/ppa\nppa:stebbins/handbrake-releases\nppa:cairo-dock-team/ppa')
```

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by evilsoup on 2013-05-27
In the same vein as HilmTye's response:

```

for f in ppa:cdemu/ppa ppa:fengestad/devel ppa:tualatrix/ppa ppa:stebbins/handbrake-releases ppa:cairo-dock-team/ppa; do sudo add-apt-repository $f; done

```

---

### Post by DaveBaxter on 2013-05-27
Thanks guys (and gals), Going with sandyd's solution. (Thanks to everyone else who answered also).

---

