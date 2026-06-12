---
title: "syslog file increases every second to reach huge size rapidly"
date: 2015-12-20
forum: General Help
---

### Post by SilentSib on 2015-12-20
Hi all,

I've been using Ubuntu for quite a few years now and apart from the few problems here and there, I've always managed to find solutions to whatever problem I encountered. Today, I couldn't.

I recently upgraded to 15.10 and everything seemed to be going just fine And then, this evening, I got this notification indicating me that the space on the main hard drive where the distribution is installed was running low, which was odd as I was pretty sure that I still had quite some space left. And by space I thought about 40gb.

Not looking much into it at that moment, I was later surprised when Skype crashed during a conversation, indicating that there was no space left on the hard drive. Sure enough, I looked and there was 0gb left. I ended up trying to save up some space with apt-get autoremove and other commands and then thought I was finally out of the mess with about 40gb left.

That didn't last. After an ultimate reboot, I was stuck on the ubuntu logo that loads and loads. It was taking minutes and was obviously using up the cpu (could see the LED constantly blinking, which was odd). I once again went back to Windows and had a look at the syslog file, hoping to find an explanation to this mess. And that's then that I noticed that my syslog file had reached 65gb. WTF. I deleted it, restarted, and could finally be back on linux. But as I was suspecting, the problem wasn't solved. The file kept growing bigger and bigger by the second with the following log:

> Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: Expression error: unknown variable
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: CPU  $ ( site ( cpu.use ) )
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: ---------^
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: Expression error: unknown variable
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: CPU  $ ( site ( cpu.use ) )
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: ---------^
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: Expression error: unknown variable
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: CPU  $ ( site ( cpu.use ) )
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: ---------^
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: Expression error: unknown variable
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: CPU  $ ( site ( cpu.use ) )
Dec 21 00:36:55 sib-P15xEMx gnome-session[2909]: ---------^
Dec 21 00:36:56 sib-P15xEMx gnome-session[2909]: Expression error: unknown variable
Dec 21 00:36:56 sib-P15xEMx gnome-session[2909]: CPU  $ ( site ( cpu.use ) )



I searched for the content on google but couldn't find anything. I'm really puzzled as to what to do next. I would consider posting the whole syslog file (~400kb so far as I rebooted in time before it got too big) on pastebin if any of you guys would think it's relevant. I'm out of my depths here and would really appreciate some help. The system was working perfectly fine and I'd rather avoid to format and start from scratch now if possible.

Thanks!

SilentSib

---

