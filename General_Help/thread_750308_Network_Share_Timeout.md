---
title: "Network Share Timeout?"
date: 2008-04-09
forum: General Help
---

### Post by stim on 2008-04-09
I use my Dell D600 as a web server for a personal website that I am tinkering with (learning how to use apache, php, msql etc).  I am using Jinzora to share my music so that it is accessible when I go to work/school.   I have this line in my etc/fstab, to mount my music from another machine.

//stim-pc/My_Music  /var/www/home/music cifs  file_mode=0x755,dir_mode=0x755,iocharset=utf8,codepage=unicode,unicode  0  0

My problem is that when I take the laptop outside the home network, I obviously am not going to be mounting the share from my other machine.   When I boot ubuntu, it takes a minute or two longer than usual to boot up because it tries  to mount the share and then gives me a red error message [[COLOR="DarkRed"]FAIL[/COLOR]].
Is there a way to modify the timeout so that it will not take as long, or possibly add it to the /etc/init.d/apache2 start script so that it mounts when apache starts?  I have been using linux for about a year and a half.
Any help is appreciated.
Chris

---

