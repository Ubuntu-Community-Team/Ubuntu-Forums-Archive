---
title: "Special characters (none in terminal, disappear in Thunderbird)"
date: 2015-01-12
forum: General Help
---

### Post by Meneer Jansen on 2015-01-12
This is driving me crazy.

I use a distribution based on Ubuntu 14.04, gnome-terminal and Thunderbird ver. 31.3.0. The terminal and Thunderbird have problems w/ special characters like é (an e with an accent aigu on it). I think it's a *locale* problem... When I type a special character in Thunderbird then it shows up fine, but sometimes after saving the special characters are all replaced by strange characters. Just like you've gotten an e-mail from somebody who uses different character encoding. And when I type a command in the terminal, that gnome-terminal does not recognize, it echoes that command between quotation marks. But what I see instead of ` and ' are strange characters that look black diamons with a question mark inside it. The terminal cannot print special characters. Very weird. Some terminal based app are unreadable because of this. 

My e-mails look weird (and I look like a fool) when other people get them. Does anybody know whats the matter and how to solve this? :?

---

### Post by Meneer Jansen on 2015-01-12
I fiddled a bit w/ locales (changed to en_US in the OS-wide settings windows I could find) and added some locale info in the following files:
In ~/.bashrc:
```

export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
export LANGUAGE=en_US.UTF-8

```
In ~/.profile:
```

export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
export LANGUAGE=en_US.UTF-8

```
and in ye 'ol /etc/rc.local (some say modern Linux distro's don't use it anymore):
```

LANGUAGE="en_US.UTF-8

```
In /etc/locale.conf:
```

LC_COLLATE=en_US.UTF-8 ls -x

```
Rebooted and the terminal didn't output weird characters anymore

---

