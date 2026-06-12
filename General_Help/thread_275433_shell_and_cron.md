---
title: "shell and cron"
date: 2006-10-11
forum: General Help
---

### Post by evaristegalois on 2006-10-11
There is a little command line program called id3tool. It will fix the tags for your mp3 files. I want to record radio streaming automatically using cron and then label the resulting mp3 file with id3tool, also using cron. That way I can just harvest the radio programs as mp3 files onto my ipod. 

Here is the problem. The command

id3tool -t title -a album-name -r "Public Radio" filename.mp3

works well on the shell (Public Radio being the artist tag). However, the command in cron

15 10 11 10 * id3tool -t title -a album-name -r "Public Radio" filename.mp3

doesn't do anything at 10:15am on October 11. Why? There don't seem to be any special characters in this command that would need escaping in cron.

--evaristegalois

FOR THE SOLUTION TO THIS PROBLEM GO TO [http://www.ubuntuforums.org/showthread.php?t=277527](http://www.ubuntuforums.org/showthread.php?t=277527)

---

### Post by subzero79 on 2006-10-11
Check if the cron daemon is started

ps -e | grep cron

It seems that you need to point to the exact location of the filename in crontab like

id3tool -t title -a album-name -r "Public Radio" /home/user/Desktop/record.mp3

---

### Post by evaristegalois on 2006-10-11
I did. I should have mentioned that I used the full pathname for the file. That's not the issue.

Also, cron is working fine. I always use another command with it to make sure cron works, such as 

15 10 11 10 * echo "chron working" > /home/test.txt

Again, that doesn't solve the problem.

--evaristegalois

---

### Post by subzero79 on 2006-10-11
Well i've tested the id3tool command in cron and worked for me. I used a regular mp3 file and removed the original tag. Try testing another mp3 file.

---

### Post by evaristegalois on 2006-10-15
The solution to the problem is posted on [http://www.ubuntuforums.org/showthread.php?t=277527](http://www.ubuntuforums.org/showthread.php?t=277527).

Thanks for your help.

--evaristegalois

---

