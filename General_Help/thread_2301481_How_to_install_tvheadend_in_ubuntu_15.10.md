---
title: "How to install tvheadend in ubuntu 15.10"
date: 2015-11-02
forum: General Help
---

### Post by fkervin on 2015-11-02
Hi all,

I've try to install TVHeadend in Ubuntu 15.10 in the same way I did in 14.04:

curl [http://apt.tvheadend.org/repo.gpg.key](http://apt.tvheadend.org/repo.gpg.key) | sudo apt-key add -
sudo apt-add-repository [http://apt.tvheadend.org/stable](http://apt.tvheadend.org/stable)
sudo apt update
sudo apt install tvheadend

The problem is in the last step, I have a error message saying package does not exist. I think it must be becouse this program has still not beign compiled for 15.10, and I have to compile it by myself or downloading the installer. I'm not sure how to do this, anyone can help?

Many thanks in advance

Regards

---

### Post by QDR06VV9 on 2015-11-02
You could change the PPA from wily to trusty that seems to be where they stopped.
I would be very watchful of what gets removed or installed.
Seems it has not had a lot of attention since 2014
[http://apt.tvheadend.org/stable/dists/trusty/](http://apt.tvheadend.org/stable/dists/trusty/)
22-Apr-2014 11:11 
Proceed at your own risk.
Kind Regards

---

### Post by fkervin on 2015-11-02
Many thanks. How could I do it? (change the PPA).

I want it to take effect only on TVheadend, not other programs.

thanks again

---

### Post by QDR06VV9 on 2015-11-02
You would change [COLOR=#545454][FONT=arial]your **/etc/apt/**[/FONT][/COLOR]**[COLOR=#6A6A6A][FONT=arial][B]sources**[/FONT][/COLOR][COLOR=#545454][FONT=arial].[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial][B]list
[/B][/FONT][/COLOR][/B][COLOR=#6A6A6A][FONT=arial]**So you could open the terminal and "gksudo gedit **[/FONT][/COLOR]**[COLOR=#545454][FONT=arial]/etc/apt/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]sources[/FONT][/COLOR][COLOR=#545454][FONT=arial].[/FONT][/COLOR]**[COLOR=#6A6A6A][FONT=arial][B]list" with out the quotes.
[/B][/FONT][/COLOR]```
[COLOR=#6A6A6A][FONT=arial]**gksudo gedit **[/FONT][/COLOR]**[COLOR=#545454][FONT=arial]/etc/apt/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]sources[/FONT][/COLOR][COLOR=#545454][FONT=arial].[/FONT][/COLOR]**[COLOR=#6A6A6A][FONT=arial]**list**[/FONT][/COLOR]
```
I used gedit here I do not know what desktop you are using, so you would replace gedit with IE kate, pluma, mousepad, yada yada. 
Look for the tvheadend lines and change only the word wily to trusty.
Most PPAs have two lines main and source.
Hope that is clear enough.
Cant stress enough to watch for what will be removed or replaced.
If you are unsure post back any out-put you do not understand.

---

### Post by fkervin on 2015-11-03
Hi runrickus[COLOR=#6A6A6A][FONT=arial][B],
[/B]
Many many thanks for your reply and help. With your indications I've been able to install another program that I had with the same issue, I'll take note of this workaround ;)

Unfortunately tvheadend does not work as it should, I don't know if you could help me with this, but at least I'll tell it.

I added the lines to [COLOR=#6A6A6A][FONT=arial][/FONT][/COLOR][COLOR=#545454][FONT=arial]/etc/apt/[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]sources[/FONT][/COLOR][COLOR=#545454][FONT=arial].[/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]list as you told me, and then I could install TVheadend. Then I can go to browser and navigate to "localhost:9981" correctly, enter username and password specified on installation and I enter on web menu with no issues.

The problem comes when I restart computer, for some reason I don't know in this moment I cant access [COLOR=#6A6A6A][FONT=arial][COLOR=#6A6A6A][FONT=arial]"localhost:9981", the URL is not found (tvheadend service not running?). Then I run from terminal "tvheadend" and it seems to active:[/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR]
[/FONT][/COLOR]```
ubuntupc@ubuntupc:~$ tvheadend
nov 03 14:56:11.027 [   INFO]:charset: 71 entries loaded
nov 03 14:56:11.027 [   INFO]:dvb: Found adapter /dev/dvb/adapter0 (Realtek RTL2832 (DVB-T)) via USB (480 Mbit/s)
nov 03 14:56:11.029 [   INFO]:CSA: Using SSE2 128bit parallel descrambling
nov 03 14:56:11.029 [   INFO]:epggrab: module eit created
nov 03 14:56:11.029 [   INFO]:epggrab: module uk_freesat created
nov 03 14:56:11.029 [   INFO]:epggrab: module uk_freeview created
nov 03 14:56:11.029 [   INFO]:epggrab: module viasat_baltic created
nov 03 14:56:11.039 [   INFO]:epggrab: module opentv-skyuk created
nov 03 14:56:11.039 [   INFO]:epggrab: module opentv-ausat created
nov 03 14:56:11.039 [   INFO]:epggrab: module opentv-skyit created
nov 03 14:56:11.041 [   INFO]:epggrab: module pyepg created
nov 03 14:56:11.041 [   INFO]:epggrab: module xmltv created
nov 03 14:56:16.909 [   INFO]:epggrab: module /usr/bin/tv_grab_uk_rt created
nov 03 14:56:16.910 [   INFO]:epggrab: module /usr/bin/tv_grab_il created
nov 03 14:56:16.910 [   INFO]:epggrab: module /usr/bin/tv_grab_dk_dr created
nov 03 14:56:16.910 [   INFO]:epggrab: module /usr/bin/tv_grab_eu_egon created
nov 03 14:56:16.910 [   INFO]:epggrab: module /usr/bin/tv_grab_fi created
nov 03 14:56:16.910 [   INFO]:epggrab: module /usr/bin/tv_grab_no_gfeed created
nov 03 14:56:16.910 [   INFO]:epggrab: module /usr/bin/tv_grab_dtv_la created
nov 03 14:56:16.910 [   INFO]:epggrab: module /usr/bin/tv_grab_huro created
nov 03 14:56:16.910 [   INFO]:epggrab: module /usr/bin/tv_grab_ar created
nov 03 14:56:16.910 [   INFO]:epggrab: module /usr/bin/tv_grab_na_dtv created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_na_tvmedia created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_is created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_eu_epgdata created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_pt_meo created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_uk_tvguide created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_se_swedb created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_fi_sv created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_it created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_fr_kazer created
nov 03 14:56:16.911 [   INFO]:epggrab: module /usr/bin/tv_grab_combiner created
nov 03 14:56:16.912 [   INFO]:epggrab: module /usr/bin/tv_grab_ch_search created
nov 03 14:56:16.912 [   INFO]:epggrab: module /usr/bin/tv_grab_uk_atlas created
nov 03 14:56:16.912 [   INFO]:epggrab: module /usr/bin/tv_grab_na_dd created
nov 03 14:56:16.912 [   INFO]:epggrab: module /usr/bin/tv_grab_tr created
nov 03 14:56:16.912 [   INFO]:epggrab: module /usr/bin/tv_grab_nl created
nov 03 14:56:16.912 [   INFO]:epggrab: module /usr/bin/tv_grab_za created
nov 03 14:56:16.912 [   INFO]:epggrab: module /usr/bin/tv_grab_hr created
nov 03 14:56:16.912 [   INFO]:epggrab: module /usr/bin/tv_grab_es_laguiatv created
nov 03 14:56:16.912 [   INFO]:epggrab: module /usr/bin/tv_grab_uk_bleb created
nov 03 14:56:16.913 [   INFO]:epggrab: module /usr/bin/tv_grab_fr created
nov 03 14:56:16.913 [   INFO]:epggrab: module /usr/bin/tv_grab_se_tvzon created
nov 03 14:56:16.913 [   INFO]:epggrab: module /usr/bin/tv_grab_pt created
nov 03 14:56:16.913 [   INFO]:dvr: Creating new configuration ''
nov 03 14:56:16.913 [WARNING]:dvr: Output directory for video recording is not yet configured for DVR configuration "". Defaulting to to "/home/ubuntupc". This can be changed from the web user interface.
nov 03 14:56:16.914 [ NOTICE]:START: HTS Tvheadend version 3.4.28~geb79aee~trusty started, running as PID:1801 UID:1000 GID:1000, settings located in '/home/ubuntupc/.hts/tvheadend'
nov 03 14:56:17.884 [   INFO]:AVAHI: Service 'Tvheadend' successfully established.
nov 03 14:56:20.173 [  ERROR]:HTTP: 127.0.0.1: /extjs.html -- 401
nov 03 14:56:21.904 [  ERROR]:HTTP: 127.0.0.1: /extjs.html -- 401
nov 03 14:56:22.904 [  ERROR]:HTTP: 127.0.0.1: /extjs.html -- 401
nov 03 14:56:23.517 [  ERROR]:HTTP: 127.0.0.1: /extjs.html -- 401[COLOR=#6A6A6A][FONT=arial][/FONT][/COLOR]
```

Now I can enter [COLOR=#6A6A6A][FONT=arial][COLOR=#6A6A6A][FONT=arial][COLOR=#6A6A6A][FONT=arial][COLOR=#6A6A6A][FONT=arial]"localhost:9981", but the username/pass that I used on installation doesn't work, so I can't access web interface :(. I have even try to create a new user/pass before the first restart (when I can enter web-menu)[/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR] but after restart it doesn't work.

So, it seems that after restarting computer the service is not able to run automatically on startup, and what is worse, even when I can run manually, it doesn't recognize users.

I'd be very thank if someone can help.

Regards

---

### Post by QDR06VV9 on 2015-11-03
@fkervin
I am very sorry, I am clueless on this program I have no experince with this. But thier forums might be a good place for your questions.
[https://tvheadend.org/projects/tvheadend/wiki/Install_and_initial_setup](https://tvheadend.org/projects/tvheadend/wiki/Install_and_initial_setup)
Edit: Maybe this will help don't know for sure but was common for wily.
```
[COLOR=#484848]sudo apt-get install --reinstall perl perl-modules perl-base[/COLOR]
```
Best of Luck 
Kind Regards

---

### Post by fkervin on 2015-11-04
Many thanks again for your interest and help, runrickus.

Your command has not solve this :(. I've found that the problem is related to the changes Canonical has made to the startup routines (systemd vs upstart) but I don't know how to solve.

I've found that I can run in terminal "**dpkg-reconfigure tvheadend**", then I reenter user/pass then it works. The problem is I have to do this everytime I restart the computer. It would be great if where is any way to enter automatically user and pass adding something to this command. If so, I could program it to run on system boot.

If I find the solution I'll tell :)

Regards

---

### Post by fkervin on 2015-11-04
Solved!

I've stop tvheadend and create a superuser file in /home/myuser/.hts/tvheadend with this content:

   {
"username": "usernamehere",
"password": "passwordhere" 
}

Then do sudo chown hts:hts /home/myuser/.hts/tvheadend/superuser.

Regards

---

### Post by QDR06VV9 on 2015-11-04
> **fkervin said:**
> Solved!

I've stop tvheadend and create a superuser file in /home/myuser/.hts/tvheadend with this content:

   {
"username": "usernamehere",
"password": "passwordhere" 
}

Then do sudo chown hts:hts /home/myuser/.hts/tvheadend/superuser.

Regards
Great Detective work:D, Good Job and Thanks for sharing your method ;) 
You might consider marking your thread Solved using the thread tools below link will show you how.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
To help other's that may have similar problems.
Best Regards

---

### Post by fkervin on 2015-11-09
Of course!

Many thanks! :)

---

