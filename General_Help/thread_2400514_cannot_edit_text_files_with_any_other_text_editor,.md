---
title: "cannot edit text files with any other text editor, something odd with permissions"
date: 2018-09-06
forum: General Help
---

### Post by iiidefconiii on 2018-09-06
Hi,

ubunru 18.04.1 LTS
GNOME 3.28.2

i have 2 users 
htpc
homeassistant

I recently installed ubuntu and im a noob at linux, i just know basic, basic, like reall basic, cp, mv, sudo, that kinds of stuff.
I made my way to get a few programs and services running.[IMG]https://imgur.com/a/3lHeTXW[/IMG] Im also unable to edit the folder permission or create a samba share.

im always logged in as htpc:
id:
```
uid=1000(htpc) gid=1000(htpc) groups=1000(htpc),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)[
```
I can edit the files with the default text editor from ubuntu and save them in the directory:
```
~homeassistant/.homeassistant/ui-lovelace.yaml
```

but i cannot do this with either notepad-plus-plus nor notepadqq editors from the ubuntu software even the titlebar of notepad++ says [Administrator]
it simply says access denied.

```
ls -l ui-lovelace.yaml
-rw-rw-r-- 1 htpc htpc 3197 sep  6 22:52 ui-lovelace.yaml
```
```
ls -ld .
drwxrwxr-x 11 homeassistant adm 4096 sep  6 23:06
```

Im not getting anything back from:
```
touch ~homeassistant/.homeassistant/my-test-file.txt
```
```
touch ~homeassistant/.homeassistant/ui-lovelace.yaml
```
[https://image.ibb.co/mzGa5K/1.png](https://image.ibb.co/mzGa5K/1.png)

[https://s22.postimg.cc/nxsk4hx75/image.png](https://s22.postimg.cc/nxsk4hx75/image.png)

[https://s22.postimg.cc/ke6mermsh/image.png](https://s22.postimg.cc/ke6mermsh/image.png)
[https://s22.postimg.cc/6x9nw67ep/image.png](https://s22.postimg.cc/6x9nw67ep/image.png)

---

### Post by Impavidus on 2018-09-06
Your notepad* text editor is installed as a snap package. It's the only way this editor is available on Ubuntu. Snaps are completely sandboxed, and for good reason, so they can't get to the home directory of another user, even when you attempt to run them as root. I suggest you use a different text editor.

BTW, it's generally a bad idea to run GUI programs with sudo. It tends to change permissions and ownership of files belonging to the GUI, breaking the GUI and preventing you from logging in. There are some workarounds and of course terminal based text editors.

---

### Post by iiidefconiii on 2018-09-07
thanks for the information
do you know any good text editor thats a bit simulair as notepad++ that would work?

---

### Post by HermanAB on 2018-09-07
$ sudo apt install geany

---

### Post by cariboo on 2018-09-07
I'm running home assistant here on a raspberrypi, all the files in the ~/homeassistant/.homeassistant directory should be owned by homeassistant:homeassistant:

```
ls -la
total 551848
drwxr-xr-x 6 homeassistant homeassistant      4096 Sep  7 10:47 .
drwxr-xr-x 4 homeassistant homeassistant      4096 Sep  3 14:48 ..
-rw-r--r-- 1 homeassistant homeassistant       222 Sep  3 21:16 .alias
-rwxr-xr-x 1 homeassistant homeassistant       753 Jun 24 01:00 automations.yaml
-rwxr-xr-x 1 homeassistant homeassistant     16523 Feb 11  2018 battery_alert.yaml
-rwxr-xr-x 1 homeassistant homeassistant      4870 Jan 15  2018 broadlink.yaml
-rwxr-xr-x 1 homeassistant homeassistant       124 Jul 23 23:30 check_config
drwxr-xr-x 2 homeassistant homeassistant      4096 Sep  3 16:49 .cloud
-rw-r--r-- 1 homeassistant homeassistant      2711 Sep  4 22:58 configuration.yaml
-rw-r--r-- 1 homeassistant homeassistant      1873 Sep  3 20:59 customize.yaml
drwxr-xr-x 2 homeassistant homeassistant      4096 Sep  3 14:48 deps
-rwxr-xr-x 1 homeassistant homeassistant       380 Aug  8 12:26 fan.yaml
-rwxr-xr-x 1 homeassistant homeassistant       409 Jul 29 15:04 google_calendars.yaml
-rwxr-xr-x 1 homeassistant homeassistant       177 Jan 28  2018 graphing
-rwxr-xr-x 1 homeassistant homeassistant      2963 Aug  6 22:31 groups.yaml
-rwxr-xr-x 1 homeassistant homeassistant      1494 Oct 28  2017 groups.yaml.bak
-rwxr-xr-x 1 homeassistant homeassistant    242399 Aug  6 22:14 hass.html
-rw-r--r-- 1 homeassistant homeassistant         6 Sep  3 14:49 .HA_VERSION
-rw-r--r-- 1 homeassistant homeassistant     19997 Sep  7 10:09 home-assistant.log
-rw-r--r-- 1 homeassistant homeassistant 564649984 Sep  7 10:47 home-assistant_v2.db
-rw-r--r-- 1 homeassistant homeassistant      3302 Sep  4 18:32 known_devices.yaml
-rw-r--r-- 1 homeassistant homeassistant      2128 Sep  3 16:28 long_live_access_token.py
-rwxr-xr-x 1 homeassistant homeassistant       532 Mar 20 00:00 rf_platform.yaml
-rw-r--r-- 1 homeassistant homeassistant         0 Sep  3 14:49 scripts.yaml
-rwxr-xr-x 1 homeassistant homeassistant       174 Aug 24 12:54 secrets.yaml
-rw-r--r-- 1 homeassistant homeassistant      4015 Sep  5 13:09 sensors.yaml
-rwxr-xr-x 1 homeassistant homeassistant        47 Feb 24  2018 Sonoff RF Bridge code.yaml
drwxr-xr-x 2 homeassistant homeassistant      4096 Sep  3 18:53 .storage
-rwxr-xr-x 1 homeassistant homeassistant      5676 Apr 16 11:27 switches.yaml
-rwxr-xr-x 1 homeassistant homeassistant       315 Jun  6 13:30 tropical_night_sensor.yaml
drwxr-xr-x 2 homeassistant homeassistant      4096 Sep  3 14:57 tts
-rwxr-xr-x 1 homeassistant homeassistant      9485 Jul 10 00:17 ui-lovelace2.yaml
-rwxr-xr-x 1 homeassistant homeassistant      2044 Jul 14 15:23 ui-lovelace2.yaml.bak
-rw-r--r-- 1 homeassistant homeassistant      4108 Sep  3 17:50 ui-lovelace4.yaml
-rw-r--r-- 1 homeassistant homeassistant      4551 Sep  5 13:15 ui-lovelace.yaml
-rw-r--r-- 1 homeassistant homeassistant        44 Sep  3 14:52 .uuid
```

I have hassio running in a vm on 18:10, all the files on that install are owned by the homeassistant user too.

---

### Post by iiidefconiii on 2018-09-10
thanks this works perfect without any issues

---

