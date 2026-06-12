---
title: "exclude dir from slocate database, -u option not working?"
date: 2006-11-14
forum: General Help
---

### Post by dannyboy79 on 2006-11-14
Can anyone help me here? I used to always use the find command to find stuff, sudo find / -name blah, but some1 told me that I was thrashing my hdd, meaning that my everytime I did that my hard drive was being worked really hard. (is this true) I just assumed the guy who told me this was correct and loooked into slocate. Well, it is installed and I did sudo slocate -u (per the man page) so that my database would start at / (which I believe that my slocate db will include my entire linux hard drive. (is this true?) Now when I read the man page about excluding a dir (i don't want the db to include a backup folder that I have) I am suppose to use the -e option but it isn't working. if i do sudo slocate -e /home/blah/blah/dong, and then sudo updatedb, and then do slocate -i blah, it'll still find the filename blah within the /home/blah/blah/dong direcotry. So what am I not understanding about the -e option? Oh, I have also tried sudo slocate -e /home/blah/blah/dong/ as well, notice the / on the end. then sudo updatedb and it still looks within that directory. do i need to somehow delete the database file tyhat was created when I first did sudo slocate -u? then before I do that I need to use the -e option? Any help would be appreciated. I figured I would always use the locate function for files I know are more than a day old since the db gets auto uypdated  by cron daily, and then I would use the find function when I know the file is new and isn't in the slocate db yet. Thanks for any help!

---

