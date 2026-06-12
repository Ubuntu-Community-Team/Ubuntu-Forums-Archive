---
title: "Trying to install LAMP"
date: 2013-07-20
forum: General Help
---

### Post by korn16ftl3 on 2013-07-20
I'm trying to set up a Final Fantasy XI private server....and a prerequisite is of course LAMP
(FFXI private server guide here: [https://wiki.dspt.info/index.php/Building_the_Server](https://wiki.dspt.info/index.php/Building_the_Server) )

so im following a tutorial on how to set LAMP up ( [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) ) and i get all the way to the "[COLOR=#000000][FONT=verdana]Step 3. This is where things may start to get tricky. Begin by typing the following into Terminal: " under the MySQL instructions and type the instructed command 
[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Courier New][I]mysql -u root
[/I][/FONT][/COLOR]
```

and i get the following readout

```

 user@user-HP-2000-Notebook-PC:~$ mysql -u rootERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

If i use sudo i get:
```

user@user-HP-2000-Notebook-PC:~$ sudo mysql -u root
[sudo] password for user: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```



how do i go about making the mysql -u root work? what am i missing here?



EDIT:
nvm.....i didnt see any thing until i scrolled to the bottom and there was a link for people with error 1045: [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)
havent had much rest....perhaps its time.....if i have further issues with LAMP i will post back in this thread.....sorry if i wasted your time reading this... /facepalm

---

### Post by Cheesemill on 2013-07-20
Your missing the -p switch from the mysql command that prompts for your password. Try this...
```
mysql -u root -p
```

The tutorial you are following is 6 years old which is why the commands in it aren't working. You don't need to run the 'SET PASSWORD' command as you will have already been prompted for a mysql root password when it was installed.

In fact the entirety of the tutorial can now be accomplished with one command...
```
sudo apt-get install lamp-server^
```

---

