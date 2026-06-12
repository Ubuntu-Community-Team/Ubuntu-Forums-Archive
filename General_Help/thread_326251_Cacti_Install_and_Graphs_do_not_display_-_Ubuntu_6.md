---
title: "Cacti Install and Graphs do not display - Ubuntu 6.10"
date: 2006-12-27
forum: General Help
---

### Post by rhbowman on 2006-12-27
I hate searching and not getting an answer so here you go, this is a very dubmened down version and is not meant to provide expert security professional advice and what not.

Ok here is the setup:

You installed ubuntu 6.10 with the server CD and chose the LAMP option. Lamp stands for Linux, Apache, Mysql, Php. You also install postfix and courier because you read a tutorial.

Now you immediately want to install cacti:

apt-get install cacti

You will get a thing about adodb not being in php.ini somewhere. This is ignorable for now and ultimately the cause of why you are reading this.

Configure a few devices and setup bandwidth graphs for them

Unfortunately none of the graphs are displaying properly! Man those Ubuntu guys have to be lame-o's!

Type this: **cat /var/log/apache2/error.log**

Observe this: (with a little imagination replace corporate_switch with your device)

ERROR: opening '/usr/share/cacti/site/rra/corporate_switch_traffic_in_115.rrd': No such file or directory
ERROR: opening '/usr/share/cacti/site/rra/corporate_switch_traffic_in_121.rrd': No such file or directory

Your first reaction is there must be a permission problem with the directory. Heck there might be! We's ain't no computer wrasslers.

If you don't care or are only using this for fun type:
(give everyone the access to read and write)

chmod 777 /usr/share/cacti/site/rra

Well the very first thing you should try to do is:

[B]dpkg-reconfigure php5-mysql
[/B]

This command will also fix php not working on Edgy with apache.

and just choose yes for whatever comes up if you dont understand what it means. If you care keep reading. You may not get all these questions.

You are installing MySQL support for php5, and it is not yet enabled in the configuration for the apache2 SAPI.  Do you want this extension to be enabled now?           

Yes - improved performance and functionality
No - wont work

You are installing MySQL support for php5, and it is not yet enabled in the configuration for the cgi SAPI. 

Yes - Same as above
No - same as above

You are installing MySQL support for php5, and it is not yet enabled in the configuration for the cli SAPI.  Do you want this extension to be enabled now?

Yes - for the command line interface
No - same as above


Congratulations,

Cacti is now displaying your graphs. 


P.S. 

I am a for real IT professional.

---

### Post by KenSentMe on 2006-12-27
Maybe this thread can better be moved to the Howto section

---

### Post by flickerfly on 2007-02-27
When I run sudo dpkg-reconfigure php5-mysql, the only question I'm given is >  	
You are installing MySQL support for php5, and it is not yet enabled in the configuration for the apache2 SAPI. Do you want this extension to be enabled now?

Should MySQL be added to /etc/php5/apache2/php.ini?

<Yes>    <No>

I choose 'Yes' of course and my results are not as expected. Cacti still isn't creating the rrd files needed to make graphs.

I'm holding a conversation over here with the Cacti guys trying to debug it: [http://forums.cacti.net/viewtopic.php?p=93055](http://forums.cacti.net/viewtopic.php?p=93055)

---

