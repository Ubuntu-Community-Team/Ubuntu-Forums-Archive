---
title: "Firefox running in the background"
date: 2008-01-07
forum: General Help
---

### Post by Khane on 2008-01-07
Lately I started to get this message quite frequently :"*Firefox is still running, but is not responding. To open a new window, you must first close the exisiting Firefox process, or restart your system*". Restarting the system of course solves the problem but because I got this problem quite a lot I would like to know if there is a shorter way than logging out and in again (something like XP's ctl+ alt+delete -> "task manager" and then close Firefox and opened an other session).

This problem happens far more when I use Kubuntu than when I use XP. I am quite new to Kubuntu and I use it more and more but although I still work with XP 70% of the time this problem happened six or seven times while using Kubuntu during the last 2 days only and only once during the past 3 weeks while using XP. I would like to know if that's is a known problem between Firefox and Kubuntu that keeps Firefox running in the background so may times ? 

Second question: in the Adept Manager I did a search for "Firefox 3 Beta" and did find it; I would to know if the version I will install through using Adept Manager is the one available at [http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html) or should I download it and make a manual install (which I have still never did in Kubuntu). If so can you direct me to a link where the manual process of Firefox in Kubuntu is explained ?

Thank you very much.

---

### Post by p_quarles on 2008-01-07
Easiest thing to do is open a prompt (ctrl-F2), and type:
```
killall firefox-bin
```

---

### Post by OpenSourceFuture on 2008-01-07
Would this help?
it's called gnome-system-monitor
just bring up terminal and then

> sudo apt-get install gnome-system-monitor

I think its what your thinking of.

---

### Post by Khane on 2008-01-07
Wow ,that was a fast. 
Thank you. I'll try that next time

---

### Post by chadridesabike on 2008-01-07
if this happens in this and other programs in the futre, try ctrl+alt+backspace.  this is a very fast restart of the system that i use to kill programs.  takes like 3 seconds to be logged back in.

---

### Post by OpenSourceFuture on 2008-01-07
You can actually set it up to be started using control alt delete, but I don't know enough about scripts to help you there.

---

### Post by marmaladeskies on 2008-01-07
alt-f2

---

