---
title: ".WMV won't play"
date: 2005-05-28
forum: General Help
---

### Post by Pitbull11188 on 2005-05-28
I was wondering if anyone could help me. Whenever I try to play a .WMV file I get a message that tells me it is really a .ASF and when I change it it only plays sound not video. I'm using VLC if that makes a difference. Thanks.

---

### Post by bored2k on 2005-05-28
[QUOTE=Pitbull11188]I was wondering if anyone could help me. Whenever I try to play a .WMV file I get a message that tells me it is really a .ASF and when I change it it only plays sound not video. I'm using VLC if that makes a difference. Thanks.[/QUOTE]
 VLC won't run some of them correctly. You need mplayer/xine/totem with the right codecs.
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by NeoChaosX on 2005-05-28
bored: Yeah, the VLC problem with newer WMV codecs is pretty well known. However, that isn't his real problem. He's complaining about the message in Nautilus that says a WMV is an ASF file. This fix for *that* problem can be found [here](http://ubuntuforums.org/showpost.php?p=68816&postcount=5).

---

### Post by Pitbull11188 on 2005-05-28
Actually you are both right, I had two problems. Thanks for the help and I'm sorry about the ambiguity of the wording.

edit: In the process of attempting to fix the problem I ran into another. For some reason apt-get update is not working and I have trouble connecting to the servers. Any suggestions?

---

### Post by NeoChaosX on 2005-05-28
Just paste the contents of /etc/apt/sources.list here, so we can see what's up.

---

### Post by Pitbull11188 on 2005-05-28
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview amd64 Binary-1 (20050330)]/ hoary main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

There it is.

---

### Post by NeoChaosX on 2005-05-28
Doesn't look like anything's wrong. What happens when you do "apt-get update"? Does it complain about missing server, or does it take a long time to check all of them?

---

### Post by Pitbull11188 on 2005-05-28
It takes forever to update and then when i look at it like 20 minutes later it skipped a bunch of them.

---

### Post by NeoChaosX on 2005-05-28
Huh. I've been having problems like that, too. I get too much output that starts with "Ign" when doing an apt-get update, too. My guess is it's server problems, give it a week or so to blow over.

---

### Post by lorap on 2005-05-30
hi friend!
install this codec - gstreamer0.8-ffmpeg
this'll probably solve your problem.
at least it did to me.
have a nice day.
pavel

p.s.:
vlc's cool, i like it myself :-)

---

