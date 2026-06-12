---
title: "How to install printer (Brother DCP-1510)?"
date: 2015-11-07
forum: General Help
---

### Post by RonaldNolan on 2015-11-07
[COLOR=#141414][FONT=Open Sans]A futon is a couch and mattress in one. Throughout the day you can use it as a sofa whilst you view Tv and, when it is time to flip out the lights, you can rapidly turn it into a mattress. The most important element of a futon is the mattress simply because how comfortable it is as each a seat and bed. In this article, I will consider you via the three elements that you need to look for when it is time to purchase a new futon mattress. At the finish of the post, you will have the information you require to choose a futon mattress that will fit your needs.[/FONT][/COLOR]

[COLOR=#141414][FONT=Open Sans]Read more our articles at [/FONT][/COLOR][homepage]("http://scottxstephens.tumblr.com/")

[COLOR=#141414][FONT=Open Sans]Well, as the title suggests, we can say that this mattress mattress is truly match for a queen. This is in fact the biggest type of mattress mattress of course next to a king bed mattress. You will discover that the standard queen size mattress dimensions has the dimension of sixty" x 80". Do you know that there is an additional variation that is larger than this? Yes, it is the Olympic queen, and it is 6 inches larger that the regular queen size bed. This Olympic queen mattress has not truly reached the recognition the regular 1 has.[/FONT][/COLOR]

[IMG]http://40.media.tumblr.com/ca1da07d387ca2ea25873f1027c592c1/tumblr_inline_nxrjbbBDBZ1tt0xa0_1280.jpg[/IMG]
[COLOR=#141414][FONT=Open Sans]I would always recommend heading for the largest mattress possible for your area and requirements. The concept of utilizing a smaller mattress in a bigger area to give the concept of spaciousness seems great on paper, but doesn't pan out. Because you will be sleeping on this each evening, don't make this error. Go as big as feasible with keeping balance. You don't want to overpower your space. Kind of like closets, you can never have too large of one, can you?[/FONT][/COLOR]

[COLOR=#141414][FONT=Open Sans]Most pillows come in two sizes: Regular and King. King dimension pillows can be as well lengthy and unyielding to a person, so you might want to consider utilizing three standard pillows rather of two King dimension for a [/FONT][/COLOR][***king size mattress dimensions***]("http://scottxstephens.tumblr.com/post/132529205315/understanding-king-queen-and-full-size-mattress")[COLOR=#141414][FONT=Open Sans]. Some businesses offer a Queen dimension pillow which is often a pleased medium in between the other two sizes.[/FONT][/COLOR]

[COLOR=#141414][FONT=Open Sans]If you choose to make a wooden futon mattress, you can discover a plan concerning this in Woodworking4 Home. A wooden futon mattress is recognized to have a two way design, getting a full size mattress dimensions on top and a lower part which can be utilized as a couch seat.[/FONT][/COLOR]

[COLOR=#141414][FONT=Open Sans]The initial factor to consider when you're in the marketplace to purchase a mattress is cost. If your spending budget is higher, obviously you'll have a wider variety of options to choose from. The top mattress businesses generally use greater high quality supplies that will be more comfortable. These mattresses will also probably last lengthier than their generic counterparts. You may also want to think about buying a carefully used mattress. Often, purchasers will experience purchaser's remorse, and will quickly appear to pawn off their "too firm" or "too gentle" mattress.[/FONT][/COLOR]

[COLOR=#141414][FONT=Open Sans]Most parents hassle about the safety of new bunk beds because 1 infant will have to fall asleep four or five feet off the floor. The exceptional information is that significant accidents and injuries are astonishingly uncommon. Most are the outcome of horseplay and only mothers and fathers can verify if their kids are mature enough for bunk beds.[/FONT][/COLOR]

[COLOR=#141414][FONT=Open Sans]When you include it all up, life time cribs make a lot of sensible sense. Whether or not you determine to go with an upscale design like the Bratt Decor Chelsea Life time crib or an easier infant mattress truly depends on how a lot quality you want to spend for and if it will make you happy to be passing this crib onto your grandchildren some day.[/FONT][/COLOR]

[COLOR=#141414][FONT=Open Sans]Source: [/FONT][/COLOR]***[http://scottxstephens.tumblr.com/post/133139842610/what-tends-to-make-a-futon-mattress-so](http://scottxstephens.tumblr.com/post/133139842610/what-tends-to-make-a-futon-mattress-so)***

---

### Post by QDR06VV9 on 2015-11-07
See if this helps [http://tutorialforlinux.com/2015/06/08/how-to-install-brother-dcp-1510-printer-drivers-on-ubuntu-15-04-vivid-32-64bit-gnu-linux-easy-guide/](http://tutorialforlinux.com/2015/06/08/how-to-install-brother-dcp-1510-printer-drivers-on-ubuntu-15-04-vivid-32-64bit-gnu-linux-easy-guide/)
Looks pretty straight forward.
Regards and Good Luck

---

### Post by SeijiSensei on 2015-11-07
Go to this page: [http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=dcp1510_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=dcp1510_eu_as&os=128) and download the "driver install tool."  If you use Firefox or some other standard browser, choose "Save" and it should be stored in the "Downloads" folder in your home directory.

Open a Terminal, then run these commands:
```

cd ~/Downloads
gunzip linux-brprinter-installer-2.0.0-1.gz
chmod u+x linux-brprinter-installer-2.0.0-1
sudo ./linux-brprinter-installer-2.0.0-1

```
That will unpack the "gzip" archive and create a file called linux-brprinter-installer-2.0.0-1.   The "chmod" command makes the file "executable," and the final command runs the program.  The "sudo" command runs the program as the "root" user, the one with administrative privileges.  You will need to enter your login password when prompted.  The installer will ask you a couple of questions and install the driver.

---

