---
title: "Boot screen splash flickers when booting"
date: 2019-08-15
forum: General Help
---

### Post by jfpolacko on 2019-08-15
Hey everyone I have a old HP DV6 with Intel® Core™ i5 CPU M 460 @ 2.53GHz × 4 and Intel® Ironlake Mobile Graphics card. I have a issue where when I boot and I get to the Ubuntu splash screen and it hang's up and flickering and just freezes up. I have to hard reboot twice and it will boot normal into Ubuntu. Any Idea's as to what could cause this and how to fix it? I'm somewhat new.. Thanks!!!

---

### Post by joris_donders2 on 2019-08-15
try the following maybe that helps: 

```
 sudo nano /etc/default/grub 
```

go to the line where stands "quite splash" and add "nomodeset" save the file and reboot/test . 
I hope this will solve the problem

---

### Post by rudy-258 on 2019-08-15
I am also having a similar problem. [https://ubuntuforums.org/showthread.php?t=2424778](https://ubuntuforums.org/showthread.php?t=2424778)

In my case it seems to be related to having a completely full disc.

---

### Post by joris_donders2 on 2019-08-16
sorry , I edit my answer due to a typo ..... 

so basicly you'll have to add the "nomodeset" to the line "quiet splash" ---> this becomes then " quiet splash nomodeset" 

If you are unfamiliar with nano you can edit the file with gedit (a text editor standard in Ubuntu) 

So type , if you can't handle nano well: 
```
 sudo gedit /etc/default/grub
```

and change , edit, the line quiet splash (there is only one) to "quiet splash nomodeset" if you don't care for a splash just leave away quiet splash (experts way lol) 

Save and do ```
 sudo update-grub
``` in the terminal

sudo reboot and test the new setting

Should this be effective or 'just an improvement' try also in updates/settings/ tab extra drivers to see if there is a alternative driver offered : install when there is 

reboot a couple of times to see if the driver improves anything. Don't forget to re-edit the Grub file into "quiet splash" only ; the same way you edited before , and don't forget to update-grub before you retest your settings . 

May this not work at all: there are some other options as well. But first things first :popcorn:

---

### Post by joris_donders2 on 2019-08-16
@ rudy-258

Please don't hijack other person's topics . I read about your problem. But that is a total different story I guess; although you can try the tip I gave for the Topic Starter.

---

