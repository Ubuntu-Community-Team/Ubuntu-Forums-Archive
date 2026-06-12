---
title: "add www user into sudoers list and service command"
date: 2013-04-06
forum: General Help
---

### Post by charm_quark on 2013-04-06
Hi, i am developing a little  web page that gives statistical information from a service. Its web page is for an application called [Airtime]("https://www.sourcefabric.org/en/airtime/") .
In order to acquire the information from the CLI, i have to run the command "```
sudo service airtime-media-monitor status
```". and provide my root password

I however did manage to manually add the "www-data" user ( the account apache is using) using the "visudo" 
 by adding 

```
www-data localhost=nopasswd: /usr/bin/service
```

i wanted to write a script to  automate the above process, i also wanted the www user to have access to only the "airtime-media-monitor " with the "status" option only and not the whole service command.  

So the question how do i add the one service and switch only ?

---

### Post by dcstar on 2013-04-07
Allows the Apache account sudo rights is a crazy security breach. It will allow your whole system to be controlled be someone who manages to hack your web server.

---

### Post by zero2xiii on 2013-04-07
Hay,

+1 For the post about security!!!!

I would rather recommend the following, adding the command to the no password require section of the sudo list:
See here for details:
[http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password)

> 
down vote
accepted	Use the NOPASSWD directive

You can use the NOPASSWD directive in your /etc/sudoers file.

If your user is called user and your host is called host you could add these lines to /etc/sudoers:
user host = (root) NOPASSWD: /sbin/shutdown
user host = (root) NOPASSWD: /sbin/reboot

This will allow the user user to run the desired commands on host without entering a password. All other sudoed commands will still require a password.

Note! Use the command visudo to edit the sudoers file to make sure you do not lock yourself out of the system – just in case you accidentally write something incorrect to the sudoers file.

Please remember this is VERY dangerous and you should rather go about it in another way.

May I suggest running a timed script to redirect the output of the command to a file, and read the file from the webpage. If you are just "monitoring" (aka you are not interacting with) the above command, such a route will be much safer!.

Regards

---

### Post by charm_quark on 2013-04-07
> **dcstar said:**
> Allows the Apache account sudo rights is a crazy security breach. It will allow your whole system to be controlled be someone who manages to hack your web server.

that is why i wanted to give "www"  access to only one service and one switch, without giving access to the rest of the commands, is that still a security hole ?

> **zero2xiii said:**
> Hay,

+1 For the post about security!!!!

I would rather recommend the following, adding the command to the no password require section of the sudo list:
See here for details:
[http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password)



Please remember this is VERY dangerous and you should rather go about it in another way.

May I suggest running a timed script to redirect the output of the command to a file, and read the file from the webpage. If you are just "monitoring" (aka you are not interacting with) the above command, such a route will be much safer!.

Regards
well, yes i am just monitoring the application and  i can write a script instead, the problem still lies that I must sudo to get the information.

---

### Post by Cheesemill on 2013-04-07
If you change the line that you added to your sudoers file to read...
```
www-data LOCALHOST=NOPASSWD: /usr/bin/service airtime-media-monitor status
```

Then the www-data user will only be able to run the command 'sudo service airtime-media-monitor status' without being prompted for a passwd.

However, I don't believe that you even need to do this as the 'service status' command shouldn't even need to be run as sudo.
You need to use sudo with the service command if you are trying to start or stop a service, but just to get a status you can run the command as a normal user...
```
rob@raring:~$ service mysql status
mysql start/running, process 26425
rob@raring:~$ 

```

---

### Post by charm_quark on 2013-04-07
Unfortunately, it does not run without "sudo", i'm assuming that is because it gets other information from different services, the memory/processor usage, log information, etc. 

thanks

---

### Post by rnerwein on 2013-04-07
hi
if you ain't want to call your command without sudo.
follow the instructions of cheesmill and then:
alias service='sudo /usr/bin/service'
try: type service ---> service ist ein Alias von `sudo /usr/bin/service'
and you get rid of your sudo ;-)
ciao

---

### Post by SeijiSensei on 2013-04-07
> **zero2xiii said:**
> May I suggest running a timed script to redirect the output of the command to a file, and read the file from the webpage. If you are just "monitoring" (aka you are not interacting with) the above command, such a route will be much safer!.

+100 for this method

Create an entry in root's crontab that runs the command and directs the output to a file in /var/www.  (Use "sudo crontab -e" for this task.  If you have a preferred editor like nano, type the command "export EDITOR=nano" before running crontab.)   Do not give the Apache server process root privileges especially if this is a machine that is visible over the Internet.

---

### Post by charm_quark on 2013-04-07
@SeijiSensei :

well i cant put it in the contrab, as the information is on request bases, so if i put it in the contrab, the information might be a little old (I'm building an API) .. that is why i having the debate of how best to solve the problem, of giving  access or not to www .. or if there is another way in php may be...... 


@rnerwein: 

:), the problem is not with the typing of sudo, as it will be part of  either the script or php code that will run on calling it but how to call it, the thing is i want to have as little as possible alteration of the system.

---

### Post by SeijiSensei on 2013-04-07
Why cannot it be a little old?  How old is "old"?  Crontab scripts run can run as often as once per minute; isn't that frequently enough?

---

### Post by charm_quark on 2013-04-09
sorry late reply, i suppose 1 min would not make much difference.

---

