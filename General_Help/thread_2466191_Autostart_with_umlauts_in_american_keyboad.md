---
title: "Autostart with umlauts in american keyboad"
date: 2021-08-22
forum: General Help
---

### Post by stabsgefreiter on 2021-08-22
I ve an american keyboard on my notebook but I need german umlauts. I configured that in the xmodmap ( which is in home directory )  and with
 xmadmap .Xmodmap   
 in terminal I can write with the umlauts. I don t want to enter the  comands every time in the terminal when using the notebook, so I need a script that would do it. I  am quite new in the linux world so I need some help.
     

The simplest way to accomplish this would be to add the command to your ~/.bashrc file:

 echo 'xmodmap ~/.Xmodmap' >> ~/.bashrc

but I dont want  to open the terminal every time, I want its done automatically when starting the notebook. So I need I script that would  do that when starting the notebook. So I need some help.
                
–

---

### Post by guiverc on 2021-08-22
also asked at [https://askubuntu.com/questions/1359437/autostart-with-umlauts-in-american-keyboad](https://askubuntu.com/questions/1359437/autostart-with-umlauts-in-american-keyboad)

---

### Post by stabsgefreiter on 2021-08-22
But the proposed solution is not that what I want

---

### Post by GhX6GZMB on 2021-08-22
You've asked this question on several forums, and it's still unclear what you're trying to achieve.
Which keys/keysequences should give you the umlauts?
On an international keyboard it would be ¨ followed by a to generate ä. Is this what you want? Then you just need to define a ¨ key on your keyboard, eg, the right Alt key.

---

### Post by Topsiho on 2021-08-22
I always use an international American keyboard, with dead keys, and have no problems at all with ä, é, û and such.
It also works in the terminal: topsiho@tambora: $ û, é, à if you need that. Just first press the dead key ("), and then the letter, such as a, to get the ä.

Topsiho

---

### Post by guiverc on 2021-08-22
I'm unclear as to your software stack, you have put it in Lubuntu on this forum (ie. LXQt most likely) but on askubuntu there was no mention of that (thus GTK3 is more likely) but we still don't know release. 

Prior solutions suggested solutions that run on opening of a terminal due to file it was added to, but by using another file you can have it run on login (ie. no need to open terminal) but there are many ways of achieving this; the [Lubuntu manual has a section on autostart for example]("https://manual.lubuntu.me/stable/3/3.2/3.2.13/session_settings.html"), but we don't know your OS & release and what you've provided is unclear (*and contradicts across sites as I've mentioned here*).

(*again I don't know release; so the manual link I provided is for latest stable or 21.04*)

---

