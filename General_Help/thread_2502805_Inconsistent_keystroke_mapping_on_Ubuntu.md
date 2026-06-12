---
title: "Inconsistent keystroke mapping on Ubuntu"
date: 2024-11-30
forum: General Help
---

### Post by gorillasvm on 2024-11-30
[]("https://unix.stackexchange.com/posts/787441/timeline")I have an Ubuntu (22.04.4 LTS with GNOME 42.9) system on my Oracle  Cloud to which I am connecting through NoMachine on two different  devices (Win11 and iPad).


As an example, when I enter the following three characters: Shift + 1, Shift + 2, Shift + 3

 On the Ubuntu system, in like a web browser, I get:

 
[LIST]
[*]when connected through windows: !@£
[*]when connected through iPad: 1"3
[/LIST]
 
I checked the "xev -event keyboard" results on terminal and this is what I found (left is windows, right is ipad): [https://imgur.com/a/weGZfAG](https://imgur.com/a/weGZfAG)

 In the above testing, my keyboard layout setting on Ubuntu was unchanged the entire time. So, my observations are:
 
[LIST]
[*]When connected through iPad, what is getting typed into the web  browser differs from what the XLookUpString from the xev terminal result  is showing (except Shift+2)

[*]For some reason, the mapping for Shift+2 seems to be different  when connecting via Windows or iPad despite the keyboard layout setting  in Ubuntu not changing

[*]The timestamp for the KeyPress and KeyRelease events via iPad is  the exact same for Press Shift, Press 1, Release 1, Release Shift, but  via Windows it is not the same, each event happens a little after the  other


[/LIST]
 What is going on here, and how can I fix this? This is just one  example of the issue. As of right now, via iPad I haven't found a way to  enter the symbols (like !,@,£,% etc) and also Shift + Alphabet is not  capitalizing the alphabet (although again in the XLookUpString result  from the xev terminal command, it shows the capital letter). Any help  would be appreciated!

---

