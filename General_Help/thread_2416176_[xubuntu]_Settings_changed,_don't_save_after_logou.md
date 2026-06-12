---
title: "[xubuntu] Settings changed, don't save after logout."
date: 2019-04-06
forum: General Help
---

### Post by winkielek on 2019-04-06
Hi,
I had some problems with my xubuntu 18.04. It's installed as a dualboot with my windows so i choose the system to run in my boot menu. Well, i had some small problems to solve such as:
[LIST]
[*]Time change, when logging from xubuntu back to windows
[*]VertScroll in xubuntu, even i changed that in xubuntu settings they didn't apply
[*]Bluetooth audio bad quality
[/LIST]
Although i managed to solve all those problems, 1st one actually i don't really remember how, 2nd one by typing synclient VertScrollDelta=-77 (the clue was the negative value), 3rd one by changing bluetooth card profle to a2dp by typing command pacmd set-card-profile 3 a2dp_sink. But even though i did all that stuff, i have to repeat doing this every shutdown, because these settings go back to default ones. It gets really annoying. I tried to run those commands in a script that runs every bootup, but it didin't work. Is there any way to keep these settings saved, so that i don't have to change them every bootup?

---

### Post by huff2 on 2019-04-14
I'm not entirely familiar with the specific items that you have listed or the files that you edited to accomplish the changes. However, what you have said indicates that you are editing files that are symbolic links to other files. This means that you can edit these files but they will always go back to the default. I'm not sure which files you are making the changes to but a very simple solution is to write a script that makes these changes and set that script to run upon start-up, so you will never have to manually do it. 

I need a lot more information. Exactly what are you doing? What files are you editing? Are you doing this from the terminal? Etc. Be very specific and if you would like me to, I can write a script for you and post it here with detailed instructions on how to make it run at start up. 

Let me know.

---

