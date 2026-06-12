---
title: "Nagios errors."
date: 2005-05-05
forum: General Help
---

### Post by vehyla on 2005-05-05
I installed nagios using apt-get and I have run into several errors.  These all might be linked in some way.  But when I go to any of the links that use a CGI I get garbled gibbierish.  However if I look at it from another system I get just an error.  This makes me believe I have a problem with firefox.  (Also gotten through apt-get) Also when I look at the nagios.log file it just repeats the same error over and over so fast that it fills /var in about 20 minutes.  Here is the error.

[1115324544] Error: Could not insert retention data for host 'gw' in table 'hostretention'

Any ideas on either problem with be greatly appreciated. ](*,)

---

### Post by Xerampelinae on 2005-05-05
Nagios is midly complex software...  it has good documentation, which you should read.  It might be hard if you're a newbie.

Anyway, I think the problem is that your database is messed up or not installed.

---

### Post by vehyla on 2005-05-06
I later used another browser to access it and everything worked perfect on that side.  I eventually had permission problems and spend a few hours fighting with apache and nagios.  After that I just gave up.  I guess that is what I get for believing the folks a ubuntu would actually check the software they throw on there servers to make sure it actually works.

---

### Post by tsumi on 2005-09-28
...Or perhaps thats what you get for jumping in water 10 feet deep with cinder blocks chained to your feet. Xerampelinae is right on.
I have yet to hear about someone successfully getting apt-get to install Nagios and having any luck. Here are a few sites that have helped me out a lot.
[http://www.clarkson.edu/projects/itl/mpX52/sp2005/longca/install.html](http://www.clarkson.edu/projects/itl/mpX52/sp2005/longca/install.html)
and
[http://www.onlamp.com/pub/a/onlamp/2002/09/05/nagios.html?page=1](http://www.onlamp.com/pub/a/onlamp/2002/09/05/nagios.html?page=1)
and
[http://www.totcat.org/pages/nagios.shtml](http://www.totcat.org/pages/nagios.shtml)
Hope this helps.

---

### Post by rossigee on 2005-12-01
I don't know what you're complaining about, vehyla! It looks to me like you were running the nagios-mysql binaries, but hadn't configured your database correctly (e.g. created a nagios database, nagios database user(s), configuring your /etc/nagios/nagios.cfg etc). I got the same problem a few moments ago, but I persevered, found and read the nagios docs related to the mysql binaries (which is what I've just set up) and it was up and running in about 10-15 minutes. Nobody's fault but your own.

I think you owe Ubuntu an apology. :)

---

