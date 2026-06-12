---
title: "Diodon Not working on ubuntu 14.04"
date: 2014-05-28
forum: General Help
---

### Post by sameermw on 2014-05-28
For Ubuntu 14.04 i use **Diodon** as my clipboard manager from below PPA

```
sudo add-apt-repository ppa:diodon-team/stable
sudo apt-get update
sudo apt-get install diodon unity-scope-diodon
```

When i disable "Security & Privacy" -> "Files & Applications", nothing will be added to the clipboard history. But i need to disable this file and application usage for privacy issues. 
[ATTACH=CONFIG]253556[/ATTACH]
Is it possible to do that or is it a diodon bug. Please help me.? Thanks

---

### Post by grumblebum2 on 2014-05-29
Do you mean added in the dash or added to the actual clipboard history accessed from the panel?
What are your privacy issues for turning off recording?
You can just turn off online search.

---

### Post by sameermw on 2014-05-30
It's look like this image. Diodon doesn't keep clipboard **either top bar or Dash diodon clipboard lens**. I don't want to record **files and activity usage** on dash. i just want disable recording these activities. but when i disable it diodon doesn't work. Diodon works only when record files and application usage. Can you  understand what i mean, sorry for my bad English. Thanks

[ATTACH=CONFIG]253596[/ATTACH]

---

### Post by sao2 on 2014-05-31
There has been a similar question asked on Ask Ubuntu [http://askubuntu.com/questions/464850/diodon-does-not-save-anything-copied-to-the-clipboard](http://askubuntu.com/questions/464850/diodon-does-not-save-anything-copied-to-the-clipboard)

Unfortunately currently it is not possible to simply choose Include Clipboard in the Security and Privacy settings although this will be goal for the future. But as a workaround you can enable the recording and only include Documents. This way the clipboard will work and all other options won't be recorded.

---

### Post by pretty_whistle on 2014-05-31
I use Parcellite clipboard manager and it's not affected by that setting, in fact I have mine turned off and Parcellite still works.  Must be a bug.

---

### Post by grumblebum2 on 2014-05-31
> **pretty_whistle said:**
> I use Parcellite clipboard manager and it's not affected by that setting, in fact I have mine turned off and Parcellite still works.  Must be a bug.
No it's not a bug. 
Did some reading after **sao2's** post and diodon is designed to use zeitgeist to store clipboard history. 
Has some advantages like infinite storage, exclude password managers from adding to clipboard and 
being able to clear the clipboard history based on time.
Bump. ;)

---

### Post by sameermw on 2014-06-01
OMG, Thanks [sao2]("http://ubuntuforums.org/member.php?u=1927113")[COLOR=#000000] [/COLOR]and everyone. I can use this option, something is better than nothing. Thanks again.

---

### Post by sameermw on 2014-06-02
There is a another solution for clipboard manager lovers,** copyq** is updated and work with **Ubuntu 14.10 Utopic/14.04 Trusty/13.10 Saucy/12.10 Quantal/12.04 Precise/Linux Mint 17/16/15/14/13/**and other [B]Ubuntu derivatives.

[COLOR=#000000]Also work when [/COLOR][COLOR=#ff0000]Files and activity usage recording disabled[/COLOR][COLOR=#000000].[/COLOR]

[/B][B]To install CopyQ in Ubuntu/Linux Mint open Terminal (Press *CTRL+ALT+T*) and copy the following commands in the Terminal:
[/B]
[TABLE="class: code-table, width: 550, align: left"]
[TR]
[TH]Terminal Commands:

[/TH]
[/TR]
[TR]
[TD]sudo add-apt-repository ppa:noobslab/indicators[/TD]
[/TR]
[TR]
[TD]sudo apt-get update[/TD]
[/TR]
[TR]
[TD]sudo apt-get install copyq[/TD]
[/TR]
[/TABLE]








More[ Info]("http://www.noobslab.com/2014/06/copyq-clipboard-manager-v22-released.html")
source [http://www.noobslab.com](http://www.noobslab.com)

---

