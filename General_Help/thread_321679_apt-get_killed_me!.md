---
title: "apt-get killed me!"
date: 2006-12-19
forum: General Help
---

### Post by stabface on 2006-12-19
hi,

so i screwed myself and need to get back up and running but need help. 

i found a list on the internet of edgy source.list 
and  i used that to update my source . list 
i wanted to have all of the restricted and back port stuff, 

any way it told me i had a bunch of updates so i upgraded them all and when i restarted x wouldn't start. 

i have my fair share of X problems so i switched the driver to "nv" 

and i was back up and running, but only one of my two moniters and now my nvidia drivers wont work because it complains that my nvidia driver and X modules are differant verisions. 

i think the modules is like 9645 or something. 

what is seem i need to do is downgrade on of them. 

i would really like some help,

---

### Post by bapoumba on 2006-12-19
Not sure I can help all the way, but some information will be needed. Can you post the output of **cat /etc/sources.list** ? How did you update, with synaptic, apt-get or aptitude ? There is a history file in synaptic (> File > Synaptic), and one also for aptitude. Which packages were updated ?

Please check this thread, it may also help you out :
[http://ubuntuforums.org/showthread.php?t=318206]("http://ubuntuforums.org/showthread.php?t=318206")

---

### Post by stabface on 2006-12-20
Thanks for the Reply, 

i think the direction need to head is figure out why my nvidia is not work. i know it has something to do with two verison being different but i am not sure how to fix it.

---

### Post by stabface on 2006-12-20
oh i just checked that thread that is my exact problem thank you !

---

