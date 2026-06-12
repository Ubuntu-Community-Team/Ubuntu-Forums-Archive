---
title: "Gis-weather"
date: 2016-06-28
forum: General Help
---

### Post by hbw1770 on 2016-06-28
Was googling for a weatherapp to install in xenial on my MSI GT72 laptop and found [Gis-Weather]("http://sourceforge.net/projects/gis-weather/") widget anda lot of info about how good it is somI installed it strictly according to thee instructions on its web site. When  I then ran it my machine completely froze and I had to repeatedly push the power button to even turn it off. When I tried to boot again later that day, it would not boot, but produced a number of error messages and at the end of those said to press Control-D, but nothing happened when I did so. Each time I turned it off and on again, the same error messages appeared  even after trying to use "recovery". I had to re-install xenial from media to get my ubuntu working again. I repeat, I installed the widget strictly according to the instructions on their web site. So my suggestion is:- IF YOU ARE RUNNING 16.04, DO NOT EVER INSTALL AND TRY TO RUN Gis-Weather, IT WILL TRASH YOUR  YOUR SYSTEM COMPLETELY.

---

### Post by ajgreeny on 2016-06-28
I may have been the hard shutdown that caused your problem rather than this weather widget.

I have no idea about Gis-weather, nor its safety on you system, but I note there have been only 230 downloads, so not a very well tested widget so far.

You may have been able to overcome your problem by booting to a live system and running a filecheck from that on your root partition with command ```
sudo e2fsck /dev/sdx#
``` where sdx#is your root partition but it is too late for that now.  Bear that it mind if you get that type of error in future.

Also remember that this is the type of problem that nobody can guard against if you install packages from third parties, not from the repos.

---

### Post by yancek on 2016-06-28
Some info on what Ctrl + D does and why it didn't help your situation.

[http://unix.stackexchange.com/questions/110240/why-does-ctrl-d-eof-exit-the-shell](http://unix.stackexchange.com/questions/110240/why-does-ctrl-d-eof-exit-the-shell)

Any particular reason why you didn't post any of the errors you saw?  I'd agree that using software from outside repositories is always riskier.

---

