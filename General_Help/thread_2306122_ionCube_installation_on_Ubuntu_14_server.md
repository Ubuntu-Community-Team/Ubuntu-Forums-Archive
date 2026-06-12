---
title: "ionCube installation on Ubuntu 14 server"
date: 2015-12-12
forum: General Help
---

### Post by Lunar_man on 2015-12-12
[COLOR=#282828][FONT=helvetica]I have some problem with locate my ioncube loader and move it.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]I have PHP 5.5.9-1ubuntu4.14[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]I have download and unpack my ionCube in tmp[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica][FONT=Menlo]root@ubuntu:/tmp# tar zxvf ioncube_loaders_lin_x86-64.tar.gz[/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.0.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_4.3.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_4.2.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.6.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.3.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/USER-GUIDE.md[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.5_ts.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.4.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/loader-wizard.php[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_4.3_ts.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.5.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/LICENSE.txt[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.4_ts.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.3_ts.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_4.4.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_4.4_ts.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.2.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/USER-GUIDE.txt[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_4.1.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/README.txt[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.1_ts.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.0_ts.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.1.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.6_ts.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]ioncube/ioncube_loader_lin_5.2_ts.so[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo] [/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo] [/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]i have created a new map here /usr/local/ioncube[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo] [/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]Now i want to move my ioncubeloader to this map but it tell me there is no file or map to move to[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo] [/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]i use this to move it but with no succes.[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]cp /tmp/ioncube/ioncube_loader_lin_5.5_ts.so /usr/local/ioncube/[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo] [/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]What am i doing wrong here? Im new to this so please have some understanding.[/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo] [/FONT][/COLOR]
[COLOR=#282828][FONT=Menlo]Anyone?[/FONT][/COLOR]

---

### Post by Lunar_man on 2015-12-12
Solved!

Thanks! have a nice day to you all guys.

---

### Post by dragonfly41 on 2015-12-12
It might be that you have unpacked ioncube into /root/tmp

Try unpacking in user mode.

You can find files by running

sudo updatedb

wait for _some time_ (long minutes) until your filesystem has been indexed

then you can run

sudo locate ioncube

---

### Post by bapoumba on 2015-12-12
> **Lunar_man said:**
> Solved!

Thanks! have a nice day to you all guys.

Well, two things would help : post the solution so that others benefit, and mark the thread as Solved once you've posted it (under Thread Tools), thanks :)

---

### Post by Lunar_man on 2015-12-12
Sorry not solved! But now what to do?

I moved my **ioncube/ioncube_loader_lin_5.5.so** to [B]/usr/lib/php5/20121212

[/B]This is where i am right now. i have restart me server but i cant see that i have ioncube.

Is there any more step? have i miss any step?

Please anybody?

---

### Post by Lunar_man on 2015-12-12
Do i need to add something in [COLOR=#474B51][FONT=Tahoma]php.ini?[/FONT][/COLOR]

---

### Post by Lunar_man on 2015-12-12
i just made some changes to my php.ini in cd /etc/php5/apache2/
nano php.ini

zend_extension = /usr/lib/php5/20121212/ioncube_loader_lin_5.5.so

And after this i restart my 

[COLOR=#FFFFFF][FONT=Menlo]service apache2 restart[/FONT][/COLOR]

I hope this was right?

Anyone can confirm this?

---

### Post by Lunar_man on 2015-12-12
If this was right? What is the next step?

---

### Post by Lunar_man on 2015-12-12
Anyone can confirm?

---

### Post by Lunar_man on 2015-12-12
[COLOR=#DD4814][COLOR=#990303][bapoumba]("http://ubuntuforums.org/member.php?u=171805") [/COLOR][/COLOR]are you there? Maybe you can help me? I guess Admin has to be good at this?

---

### Post by dragonfly41 on 2015-12-12
[http://www.lornajane.net/posts/2012/managing-php-5-4-extensions-on-ubuntu](http://www.lornajane.net/posts/2012/managing-php-5-4-extensions-on-ubuntu)

---

### Post by Lunar_man on 2015-12-12
> **dragonfly41 said:**
> [http://www.lornajane.net/posts/2012/managing-php-5-4-extensions-on-ubuntu](http://www.lornajane.net/posts/2012/managing-php-5-4-extensions-on-ubuntu)


Sorry that didn't sort any thing that i asked.

Anyone else?

---

### Post by QDR06VV9 on 2015-12-12
Maybe this will be of help read the whole page
[https://watchmy.domains/tutorials/install-ioncube.php](https://watchmy.domains/tutorials/install-ioncube.php)
Regards

---

### Post by dragonfly41 on 2015-12-12
In post#1 you refer to
ioncube_loader_lin_5.5[COLOR=#b22222]**_ts**[/COLOR].so


In post#5 you refer to
ioncube_loader_lin_5.5.so .. _not_ ioncube_loader_lin_5.5[COLOR=#b22222]**_ts**[/COLOR].so


In post#7 you refer to
zend_extension = /usr/lib/php5/20121212/ioncube_loader_lin_5.5.so


in the tutorial (above) it refers to
ioncube_loader_lin_5.5[COLOR=#b22222]**_ts**[/COLOR].so


In my own /usr/lib/php5 directory I have ..
/20121212[COLOR=#b22222]**+lfs**[/COLOR] (not /20121212)


I would just check through these again for any typo errors.

---

### Post by Lunar_man on 2015-12-12
> **runrickus said:**
> Maybe this will be of help read the whole page
[https://watchmy.domains/tutorials/install-ioncube.php](https://watchmy.domains/tutorials/install-ioncube.php)
Regards

Yes! This one i follow already. I have done my step same as the page.

I have add my

zend_extension = /usr/lib/php5/20121212/ioncube_loader_lin_5.5.so

in

[FONT=Menlo]/etc/php5/apache2# nano php.ini

is this right?

So now it should work then?

But how can i se or know it's right? That it's working correct?[/FONT]

---

### Post by QDR06VV9 on 2015-12-12
> **Lunar_man said:**
> Yes! This one i follow already. I have done my step same as the page.

I have add my

zend_extension = /usr/lib/php5/20121212/ioncube_loader_lin_5.5.so

in

[FONT=Menlo]/etc/php5/apache2# nano php.ini

is this right?

So now it should work then?

But how can i se or know it's right? That it's working correct?[/FONT]
No that is not right..it appears you have included 'nano php.ini' with what you are telling me..
So now i'm going to have to ask you to do this
```
cd /etc/php5/apache2/
```
Then enter this in a terminal
```
nano php.ini
```
witch bring up a terminal text editor
Press Ctrl-W **and search for .so**   This will take you to the part of php.ini that mentions dynamic extensions.** Insert the following line there.** Something like this screen shot
[IMG]http://i.imgur.com/ZFge2Kp.png[/IMG]
save the changes you've made, press Ctrl + O . To exit nano, press Ctrl + X .



 Then you would put this in the terminal
```
service apache2 restart
```
And No we are not done yet, I like to do these in small steps when helping others to be sure each step is done correctly.

---

### Post by Lunar_man on 2015-12-13
Ok thanks for all tips. But i cant get it to work. I follow this step now again. Please take a lok at my step now.

I have added 2 lines in my php.ini to make sure im doing right.

[IMG]http://i66.tinypic.com/34dhrbd.png[/IMG]

And i have my ioncube loader here at 
zend_extension = /usr/local/ioncube/ioncube_loader_lin_5.5.so

[IMG]http://i63.tinypic.com/2bxlxk.png[/IMG]

But i can't get it to work. in my php info i see this but no ioncube is showing enable

[IMG]http://i64.tinypic.com/4smsf6.png[/IMG]

What can be the problem? I have restart the server by doing this. As you told me.

service apache2 restart

---

### Post by Lunar_man on 2015-12-13
It looks like i forget to add _ts at the end here but still it not working.

zend_extension = /usr/local/ioncube/ioncube_loader_lin_5.5_ts.so

Anyone have some clue what the problem is?

---

### Post by Lunar_man on 2015-12-13
Yes! I finally made it. Now my Php info look like this.

[IMG]http://i67.tinypic.com/2vj3ggm.png[/IMG]


So it is really easy actually. I uploaded the wrong ioncube. It should be this one .so

ioncube_loader_lin_5.5.so

i uploaded the one with _ts that one is not working [B]ioncube_loader_lin_5.6_ts.so

[/B]So if anybody else have the same problem make sure you upload the right one to your root folder
&#8203;ioncube_loader_lin_5.5.so

So now its solved i hope!

---

### Post by dragonfly41 on 2015-12-13
Did you miss reading post#14 which pointed to the naming error?

Mark this thread as [SOLVED]. See Thread Tools at top of this page.

---

