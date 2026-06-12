---
title: "What do the following commands mean?"
date: 2016-09-19
forum: General Help
---

### Post by tonma on 2016-09-19
Hello,
I was trying to save my html pages to /var/www to test my website on a localhost, but access was denied, so I looked online for solutions, and found this, which worked:

sudo gpasswd -a "$USER" www-data
[COLOR=#111111][FONT=Ubuntu]Correct previously created files (assuming you to be the only user of /var/www):[/FONT][/COLOR]
sudo chown -R "$USER":www-data /var/www
find /var/www -type f -exec chmod 0660 {} \;
sudo find /var/www -type d -exec chmod 2770 {} \;
Also, there was an option 2, with part of the code in it was: [COLOR=#111111][FONT=Consolas]sudo ln -sT ~/projects/foo /var/www/foo -
[/FONT][/COLOR]
What is the meaning of the different commands such as  gpasswd, ln and -sT?? etc..

Ty!

---

### Post by yetimon_64 on 2016-09-19
To find the meaning of any command on the system you can use the command "man", which gives the manual page for the command in the terminal.
For example with ln an the -sT ...
```
man ln
``` Then scroll down a bit for the "s" and "T" switches...
> ```
       -s, --symbolic
              make symbolic links instead of hard links
       -T, --no-target-directory
              treat LINK_NAME as a normal file always
```

You can use the "man" command against any of the commands you note above, eg. just the name for gpasswd telling what it is for (you can scroll further down for checking any switches etc.)...
> ```
NAME
       gpasswd - administer /etc/group and /etc/gshadow
```

Each command's man file also shows usage in the "SYNOPSIS" section and a general description in the "DESCRIPTION" section as well as details for any switches available to the command further down. 

To exit the man command display in terminal, press "q" on your keyboard and the terminal returns to a normal prompt. Cheers, yeti.

---

### Post by tonma on 2016-09-19
Thank you !

---

### Post by Habitual on 2016-09-19
> **tonma said:**
> Hello,
I was trying to save my html pages to /var/www to test my website on a localhost, but access was denied, so I looked online for solutions, and found this, which worked:

sudo gpasswd -a "$USER" www-data
sudo chown -R "$USER":www-data /var/www
find /var/www -type f -exec chmod 0660 {} \;
sudo find /var/www -type d -exec chmod 2770 {} \;
Also, there was an option 2, with part of the code in it was: [COLOR=#111111][FONT=Consolas]sudo ln -sT ~/projects/foo /var/www/foo -
[/FONT][/COLOR]
What is the meaning of the different commands such as  gpasswd, ln and -sT?? etc..

Ty!
You understand this is not advisable on anything but a **closed network**?
This routine would cause me to lose sleep on a Production, internet-facing host.

The Standards I use are (for internet-facing hosts)
```
type -d  755
type -f 644

```

403 access denied:
Could be an enabled htaccess file directive, or likely DocumentRoot can't 'read' /var/www/foo as www-data
open your terminal and issue:
```
apache2ctl -S
``` and examine the output.
it lists the enabled sites apache knows about, your foo.conf.

Compare www-data/"$USER" to DocumentRoot in the sites file.conf
Your DocumentRoot in /etc/apache2/sites-enabled/foo points to
the /var/www/<site> directory.

and www-data requires read privs recursively there.
So, let's have a look at what is owned by whom now in that location, shall we? Good.
terminal:
Look at files not owned by www-data
```
find /var/www/html/foo/ ! -user www-data/CODE]
will show files and directories. Examine it. All my servers have www-data:www-data as the o:g
If that looks right, use this for owner:
[CODE]find /var/www/foo/ ! -user www-data -exec chown www-data:www-data {} \; # Notice spacing
```

directories:
```
find /var/www/foo/ ! -user www-data -type d -exec chmod -R 755 {} \;
```
files:
```
find /var/www/foo/ ! -user www-data -type f -exec chmod -R 644 {} \;
```
[COLOR=#ff0000]**NOTE**[/COLOR]: There are or could be some known exceptions for 644/755... cgi stuff for example.

See also [https://help.ubuntu.com/community/FilePermissions#Changing_the_File_Owner_and_Group](https://help.ubuntu.com/community/FilePermissions#Changing_the_File_Owner_and_Group)
and you should be familiar with [http://manpages.ubuntu.com/manpages/trusty/man8/a2dissite.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/a2dissite.8.html) tools also.

Enjoy!

---

### Post by tonma on 2016-10-05
Thank you, but I'm really new to Ubuntu, and many of the things you wrote are really hard to comprehend (I hope you understand me, it's hard to learn those things by myself).
And now that I've already done the above code, which you said wouldn't let you sleep at night, how can I completely disable what I did and do what you said?
Will the code you provided override the previous? Or I have to do that myself? If so, how to? (Hope it's OK for you and not too much of a work)

Some of my other troubles: the [COLOR=#000000]find /var/www/html/foo/ ! -user www-data code shows what's not owned? Because it pretty much showed me all the folders there. (Or that's exactly what we will do in the following 755 and 644 commands? but how does my website work now if nothing is owned by www-data?)
[/COLOR]You also wrote [COLOR=#000000][FONT=&amp]find /var/www/foo/, but should it be [/FONT][/COLOR][COLOR=#000000][FONT=&amp]find /var/www/html/foo/?[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
What is sites file.conf? I don't have that conf file in my www folder (Or you mean to the default.conf at DocumentRoot?)

Also, in the command it's www-data:www-data because the username is www-data? (In the apache2ctl command I see User: name="www-data" < Is that the one? Does it also refer to [COLOR=#000000]www-data/"$USER"?[/COLOR] or $USER is just my Ubuntu user name?) 

Btw, what is "o:g"?

Sorry, I know I mixed a few things, but I think that they all together should help me understand your explanation

> **Habitual said:**
> 

The Standards I use are (for internet-facing hosts)
```
type -d  755
type -f 644

```



I did what you say, but I can't copy files to the directory, I still get permission denied.

Am I confusing with www-data user and my own user? for example if my Ubuntu username is "james", I should create a new user named www-data for your code to work as it is? If not I should change every www-data in your code to james?
I mean, I must be confusing between the user called 'www-data' and the user of Ubuntu, is www-data a username that I should create first thing before starting to develop? When I run the command "apache2ctl -S" I do see a username and group named "www-data".. but I think that since it doesn't exist, the code won't work so I Still can't edit the var/www. my current user is only james..

---

### Post by vradovic on 2016-10-15
www-data is group name. If you go in /etc/www/ type ls -la and paste it here.

---

### Post by tonma on 2016-10-15
Can you please explain some more to me? I just want to understand a bit more,
Right now my user name is james, but the user name and group name in "apache2ctl -S" command. (It shows as a user too, not just group)

And what does ls-la do? Doesn't it just list files? How can it help me get permissions to paste there? so how do I mate the above commands work with my user called "james".. or I need to create a separate one for that? It's all mixed for me, can you please make some order for a newbie?

Guys, anyone? I followed Habitual commands exactly, but I feel like something is missing (I still have no permissions to copy to this folder)
I think that the reason is that I gave permissions to the user www-data, but I somehow need to connect www-data to my Ubuntu user (example james), am I right? and how to do that?

EDIT: I Found this: [http://askubuntu.com/questions/365087/grant-a-user-permissions-on-www-data-owned-var-www](http://askubuntu.com/questions/365087/grant-a-user-permissions-on-www-data-owned-var-www)

You can see in the top answer, that he says to add a user, not www-data. but the ubuntu user??

EDIT2: I followed both the above code, and Habitual, but I can still not write/copy files to var/www, I just think there's a missing part, I mean, where is the part where I use my current Ubuntu user?

> **vradovic said:**
> www-data is group name. If you go in /etc/www/ type ls -la and paste it here.

```
drwxrwxr-x  3 root     www-data 4096 
drwxr-xr-x 15 root     root     4096 
drwxrwxr-x  3 www-data www-data 4096
```

(deleted date because its not in English and messing up here)

I wanted to be able to write files to var/www folder, but permission was denied. I asked here and someone suggested the following:

> Look at files not owned by www-data
```
find /var/www/html/foo/ ! -user www-data
```
will show files and directories. Examine it. All my servers have www-data:www-data as the o:g
If that looks right, use this for owner:
```
find /var/www/foo/ ! -user www-data -exec chown www-data:www-data {} \; # Notice spacing
```

directories:
```
find /var/www/foo/ ! -user www-data -type d -exec chmod -R 755 {} \;
```
files:
```
find /var/www/foo/ ! -user www-data -type f -exec chmod -R 644 {} \;
```


I did that exactly (copy paste), and I still wasn't able to copy files to var/www. I think it has something to do with that fact that he used username www-data, but I am logged in as a different Ubuntu user. So I thought I need to match it, just didn't know how. I am confused with www-data user and my Ubuntu user, and where I should change it exactly. so I found this:

```

sudo adduser <username> www-data
sudo chown -R www-data:www-data /var/www
sudo chmod -R g+rwX /var/www
```

And it worked (I can now copy that to that folder). In the <username> I added my own username and not username www-data. But it's not 755 and 644, it is something else.. How can I change it to only 755 and 644..?
and am I doing something wrong? Do I need to create a username called www-data in my Ubuntu for it to work written in the first quote?

---

### Post by oldos2er on 2016-10-16
Threads merged, since they appear to be very similar.

---

### Post by tonma on 2016-10-17
> **Habitual said:**
> 

```
find /var/www/foo/ ! -user www-data -exec chown www-data:www-data {} \; # Notice spacing
```


Enjoy!

Can someone help me with this line of code? I think it has a mistake.. the user he specifies is www-data, but www-data is a virtual user. isn't it? I am logged in with my own Ubuntu user.. shouldn't it be ```
find /var/www/foo/ ! -user <My Ubuntu User> -exec chown  www-data:<My Ubuntu User> {} \; # Notice spacing
```? instead of www-data.. because I did exactly the commands, but still can't write to var/www/html ... I think it's because I did 755 and 644 for a not-real user called www-data, when I should've done it my own user. Can someone help here? am I mistaken?

---

### Post by howefield on 2016-10-17
Again, similar threads merged.

Please stop creating threads on the same issue.

---

