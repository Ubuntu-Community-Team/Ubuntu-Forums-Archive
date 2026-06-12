---
title: "Evolution - Exchange broken"
date: 2007-01-17
forum: General Help
---

### Post by traneHead on 2007-01-17
Running Evolution on 6.10 to work with our corporate exchange server has been working since day one, until yesterday when i suddenly get "Lost connection to Evolution Exchange backend process" *all* the time. I can switch between the folders and see the mail lists, some are readable, others not (instead displaying the text "Can't get message, Lost connection to Evolution Exchange backend process").
Restarting Evolution or going off/on line has no effect. The exchange server is up and running, the web client works (as well as expected...), as well as outlook (at least that's what my colegues are telling me) 

Any ideas what could have caused this to happen?

---

### Post by dcstar on 2007-01-17
> **traneHead said:**
> Running Evolution on 6.10 to work with our corporate exchange server has been working since day one, until yesterday when i suddenly get "Lost connection to Evolution Exchange backend process" *all* the time. I can switch between the folders and see the mail lists, some are readable, others not (instead displaying the text "Can't get message, Lost connection to Evolution Exchange backend process").
Restarting Evolution or going off/on line has no effect. The exchange server is up and running, the web client works (as well as expected...), as well as outlook (at least that's what my colegues are telling me) 

Any ideas what could have caused this to happen?

Close the Evolution client and then kill off all the Evolution processes in System Manager, then restart the client.

---

### Post by traneHead on 2007-01-18
Nope, thanks for your response, but that didn't do it either... :(

---

### Post by Lesterchakyn on 2007-01-31
I'm having the same problem here, but it's happening since today in the morning.

Using Edgy here.

Any ideas??

---

### Post by nexus9k on 2007-02-01
I've been having problems with Exchange also, but mainly with the calendar and occasional freezes.  Killing all of the processes will temporarily help, but that's a less than ideal solution.  I'm back to using Entourage on my Mac until the packages become stable again.  :( 

Most recently updated packages:

[UPGRADE] app-install-data-commercial 6 -> 6.3
[UPGRADE] gnome-applets 2.16.1-0ubuntu3 -> 2.16.1-0ubuntu4
[UPGRADE] gnome-applets-data 2.16.1-0ubuntu3 -> 2.16.1-0ubuntu4
[UPGRADE] gnome-netstatus-applet 2.12.0-5ubuntu6 -> 2.12.0-5ubuntu7
[UPGRADE] gnome-panel 2.16.1-0ubuntu3 -> 2.16.1-0ubuntu4
[UPGRADE] gnome-panel-data 2.16.1-0ubuntu3 -> 2.16.1-0ubuntu4
[UPGRADE] gnome-system-tools 2.15.5-0ubuntu4 -> 2.15.5-0ubuntu5
[UPGRADE] libpanel-applet2-0 2.16.1-0ubuntu3 -> 2.16.1-0ubuntu4
[UPGRADE] libvolumeid0 093-0ubuntu18 -> 093-0ubuntu18.0edgy2
[UPGRADE] system-tools-backends 1.9.7-0ubuntu4 -> 1.9.7-0ubuntu5
[UPGRADE] udev 093-0ubuntu18 -> 093-0ubuntu18.0edgy2
[UPGRADE] volumeid 093-0ubuntu18 -> 093-0ubuntu18.0edgy2

Let me know if you need any other info to help troubleshoot.

---

### Post by nexus9k on 2007-02-02
Here is some additional data from .xsession-errors

```
(evolution-2.8:19195): libecal-WARNING **: e-cal.c:318: Unexpected response

(evolution-2.8:19195): libecal-WARNING **: e-cal.c:318: Unexpected response

(evolution-2.8:19195): libecal-WARNING **: e-cal.c:318: Unexpected response

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

(evolution-2.8:19195): calendar-gui-CRITICAL **: e_week_view_event_item_draw: assertion `wveitem->event_num < week_view->events->len' failed

```

as well as evolution-exchange-bugreport.txt

```
Memory status: size: 88076288 vsize: 0 resident: 88076288 share: 0 rss: 28049408 rss_rlim: 0
CPU usage: start_time: 1170382152 rtime: 0 utime: 1227 stime: 0 cutime:1085 cstime: 0 timeout: 142 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/evolution-exchange'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233836368 (LWP 19205)]
[New Thread -1245709408 (LWP 31972)]
[New Thread -1235121248 (LWP 19207)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6e74803 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6f1c813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#3  0xb6f1cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb71efa23 in bonobo_main () from /usr/lib/libbonobo-2.so.0
#5  0x0805b9b3 in main ()

Thread 3 (Thread -1235121248 (LWP 19207)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6e74803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb6f1c813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb6f1cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb703b7e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb6f3738f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb6f86504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb6e7e51e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 2 (Thread -1245709408 (LWP 31972)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6f8d34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7d0c1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7eb7abe in icaltimezone_array_append_from_vtimezone ()
   from /usr/lib/libecal-1.2.so.7
No symbol table info available.
#5  0xb7eb86f7 in icaltimezone_get_utc_offset ()
   from /usr/lib/libecal-1.2.so.7
No symbol table info available.
#6  0xb7eb8a4c in icaltimezone_convert_time () from /usr/lib/libecal-1.2.so.7
No symbol table info available.
#7  0xb7eb64ab in icaltime_as_timet_with_zone ()
   from /usr/lib/libecal-1.2.so.7
No symbol table info available.
#8  0x08075970 in e2k_timestamp_from_icaltime ()
No symbol table info available.
#9  0x08078977 in e_cal_backend_exchange_add_object ()
No symbol table info available.
#10 0x08078fbd in e_cal_backend_exchange_add_object ()
No symbol table info available.
#11 0x0806dc4e in e_cal_backend_exchange_calendar_get_type ()
No symbol table info available.
#12 0xb7f0509f in e_cal_backend_sync_open ()
   from /usr/lib/libedata-cal-1.2.so.6
No symbol table info available.
#13 0xb7f0515b in e_cal_backend_sync_open ()
   from /usr/lib/libedata-cal-1.2.so.6
No symbol table info available.
#14 0xb7efe7de in e_cal_backend_open () from /usr/lib/libedata-cal-1.2.so.6
No symbol table info available.
#15 0xb7f0860a in e_data_cal_get_backend ()
   from /usr/lib/libedata-cal-1.2.so.6
No symbol table info available.
#16 0xb7ef8654 in _ORBIT_skel_small_GNOME_Evolution_Calendar_Cal_open ()
   from /usr/lib/libedata-cal-1.2.so.6
No symbol table info available.
#17 0xb702fb07 in IOP_start_profiles () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#18 0xb7035c75 in ORBit_OAObject_invoke () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#19 0xb7022dbc in ORBit_small_invoke_adaptor () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#20 0xb7033916 in ORBit_recv_buffer_return_sys_exception ()
   from /usr/lib/libORBit-2.so.0
No symbol table info available.
#21 0xb7033fc2 in ORBit_recv_buffer_return_sys_exception ()
   from /usr/lib/libORBit-2.so.0
No symbol table info available.
#22 0xb701bdad in giop_thread_queue_process () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#23 0xb701c638 in giop_init () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#24 0xb6f38ce8 in g_thread_pool_push () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#25 0xb6f3738f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#26 0xb6f86504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#27 0xb6e7e51e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1233836368 (LWP 19205)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6e74803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb6f1c813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb6f1cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb71efa23 in bonobo_main () from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#5  0x0805b9b3 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

---

### Post by mikesf on 2007-02-07
My evolution was working perfectly with our exchange server and then all of sudden, I get the "lost connection to evolution exchange backend process" error two days ago. What's going on? It's so frustrating to be the "linux guy" at work at talk about how great ubuntu is, and then this happens. Novell is a big company.  F*&#ing fix the problem already! 
Does anyone even have a clue how to trouble shoot this? I've tried killing/restarting all processes... no luck.

---

### Post by ghepburn on 2007-02-09
I have the same problem on edgy. I am able to retrieve my messages from exchange for a minute or two after I first connect, then I loose the connection like others have described above. If I kill processes and restart I, again, get a short connection with the server but it is lost after a short time. This is a very annoying and I am hoping someone has a solution before too long.

---

### Post by pirulo on 2007-02-13
Sorry, this is not the solution.
It seems to be a global problem with Evolution or/and Exchange. The Windows version has the same [problem]("http://www.nnseek.com/e/novell.support.evolution/evolution_windows_exchange_backend_process_10426488t.html").
I'm using Ubuntu 6.10 and Evolution 2.8.1, all functioned well until 1 or 2 weeks ago (occasionally, some problem with the calendar but nothing serious, apparently). 
Could anyone give a clue where to look for ?
Ubuntu is so cool, I'd really like to keep on working with it AND my favorite email client program.

---

### Post by mikesf on 2007-02-16
I solved the problem: use thunderbird with lightning plugin. I need calendering/invites at work, so the lightning plugin works great. I get email invitations (to meetings etc...) and they show up in my calender. NICE!
Of course, thunderbird doesn't support MSExchange, but luckily, our mail service let's us use IMAP. I actually like these mozilla apps far better than evolution, which has ALWAYS been buggy and bloated IMHO.

---

### Post by arkepp on 2007-02-20
Hi,

try shutting down Evolution, deleting ~/.evolution/exchange, and restarting Evolution.

No settings should be lost and the mail synced the next time you connect. Let me know how it goes.

---

### Post by ghepburn on 2007-02-20
Thanks for the suggestion but it did not work for me. In my case it seems that everything is fine for after my initial sign on and transfer of information. I have configured evolution to pick up email from my exchange account every three minutes. I suspect that things go wrong after the second email check. New messages that arrive continue to be listed in my inbox and I can still compose and send email. The problem seems to be that I cannot access the full email message once the second check has been made. The only way I can make this work is to continually shutdown and restart evolution.

At first I thought this must be a local issue involving my institutions set-up but given the number of people having similar problems, I suspect it is a problem with evolution and/or the exchange connector.

---

### Post by mikesf on 2007-02-21
didn't work for me either.... still get the connection error. interestlingly enough, however..... i put edgy on my laptop at work and evolution is so far working on that one....

---

### Post by will m. on 2007-02-22
FWIW I have precisely the same problem as has been described by nearly all of you.

Evolution downloads email fine, the first time.  However, upon the second email download I get what may be a message header but no contents.  I can still send/receive just fine though.

I'm anxiously awaiting a resolution.

Will M.

---

### Post by Sergtek on 2007-02-23
I have successfully fixed my "Lost connection to Evolution Exchange backend process" issue!!

After reading countless posts and doing more damage than good I decided to play with the exchange account options in evolution.

Here's what I did:
- Changed the "Automatically check for new mail every: " option to 10 minutes from 5
- Verified that the "Automatically synchronize account locally" option was checked
- Unchecked "Apply filters to new messages in Inbox on this server"

I restarted Evolution and all worked perfectly!  I hope this helps someone else.

---

### Post by will m. on 2007-02-23
Desperate as I am to find a remedy I tried your suggestion but found that it didn't work.

I'd be interested to know why these changes might make a difference so that I might get a handle on what is actually causing the problem.  I made no recent changes to Evolution or my system.  I can only assume that it is related to some update on the MS Exchange end of things.

Will M.

---

### Post by pirulo on 2007-02-26
The solution proposed by arkepp worked for me. It is still a bit slow at starting.

---

### Post by ubergeeknz on 2007-03-06
I installed Ubuntu 6.10 earlier this week trying to get off of Windows.  I have all the apps I need right here to do my job & look after my personal needs as well ;)

Now the only thing stopping me from enjoying my ubuntu experience is the exact problem described here... 

What can I do to help resolve this issue?  I am not a developer but I have *some* programming experience and a great deal of experience as a troubleshooter/engineer.  Surely there are more than a handful of people who use evolution with exchange.  As per the other poster, I think this broke after ubuntu installed all the security updates, but I can't be sure.  

As the sysadmin for our (small) office, I can categorically state that NOTHING CHANGED ON THE EXCHANGE SERVER and that outlook / OWA is working perfectly.

I have tried all the 'fixes' (ahem) described here but nothing has helped, except perhaps to alleviate the problem for a few minutes before it stops working again.  Now even restarting does not make it work.  Also if changing obscure options 'fixes' the problem.. then there is definitely a problem.

I get  the full list of emails that are on the server, but then the dreaded error message 'Lost connection to Evolution Exchange backend process' pops up and I can't read any of them.  It's so frustrating.  Initially, it worked fine, then ubuntu installed a lot of patches (138?) and it seems to be since then it got real flakey.

I am sure this feature is crucial to would-be windows converts in the workplace, so it would be real nice to see this fixed.  Also why does it not seem possible to downgrade all my components to the originally installed versions to see if they really are the cause of this problem??

---

### Post by neurovish on 2007-03-13
I drifted in from google, and it sounds like I've found the right crowd of users with this problem.  The post above describes my situation exactly, except I am running gentoo instead of ubuntu.  In my case, evolution started doing this out of the blue without making any changes to my system.  I'm running Evolution and evolution-exchange version 2.8.3.  It worked for me when I came into work, then suddenly it didn't.

I wish some large company will come along and fix evolution...maybe even try to make friends with Microsoft so it will play nice.....oh, wait, that's what Novell claims to be doing.

---

### Post by imxuk on 2007-03-14
% evolution --force-shutdown
% cd ~/.evolution
% rm -rf `find . -name *exch* -print`

Then restarted evolution, i didnt need to readd my account; although some people report they have had to....

Warning: Before removing any files or directories you should back up your entire ~/.evolution directory just in case something goes wrong and you need to restore it.

---

### Post by chris.mccauley on 2007-03-14
I'm getting the same sorts of problems but in addition I was not getting any emails being displayed on the remote Exchange Inbox folder - all I was getting was a count of the new emails. 

To describe that more, the remote Inbox folder would be listed as Inbox (4) to indicate that there were four new emails but opening the folder would not cause the emails to be displayed. To do that I had to restart Evolution. The problem seems to have begun a week or two ago. By changing the options for synchronizing the folder and applying filters the problem seems to be resolved. I'm still getting that annoying "Lost connection to backend ..." though.

---

### Post by clacroix on 2007-03-21
Hi all.

I have also problems with 'Lost connection...' symptom. I am running Evo for more than a year now, I have upgraded versions and also Ubuntu itself a few times though. Currently I run Ubuntu 6.10 and Evolution 2.8.1 that is included. In the company I work for we use Exchange server and Outlook clients. 
Anyway, what seems to cause the problem is _strange calendar items_, I am suspecting items with _some sort of attachment(s)_. I could get back my Evo with Calendar working by opening Outlook (in MSXP VM) and deleting meeting requests I have received recently. Now it is working again. 

Hope that helps someone.
Santiago

---

### Post by chris.mccauley on 2007-03-22
Come to mention it, I get the "lost contact " message when evolution is trying to reply to a meeting request. There doesn't seem to be anything obviously wrong with the invites themselves but I will stop sending replies to these and see if the problem persists.

---

### Post by luke411 on 2007-03-22
I'm a new user of evolution, though an old user of Linux. Same problem. I don't do invites on my calendar though, and I still have the same errors. I have disabled my calendar for exchange and set my local calendar as my default to see if that would help, and I still get the "back-end" message when I first connect, though at least now I can seem to read my email in the inbox. 

I'm technically not supposed to be using my exchange server at all but discovered by accident that it works with evolution (or at least partially) but I figured the error messages were just my specific situation with my specific server. 

Oh well maybe someone will figure it out.

---

### Post by jshein on 2007-03-27
I resolved this by adding "omniverse" to my sources.list and installing the latest version of
evolution.

Nothing else worked.

My sources.list is as follows:

####################################
### Official Ubuntu Repositories ###
####################################

# Edgy Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse omniverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

# Edgy Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse omniverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

# Edgy Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse omniverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

# Edgy Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse omniverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

#Ubuntu Commercial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

## created by automatixrepo3
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
#AUTOMATIX REPOS END

---

### Post by vivabenfica on 2007-04-20
same problem as everyone else. even vainly upgraded to 7.04 hoping that this had been fixed in evolution 2.10.0 but same problem,

tried removing ~/.evolution/exchange as arkepp suggested and, so far, so good.

i'll leave it hibernating this weekend and see if evolution is up when it awakens on monday.

---

### Post by cobold0815 on 2007-05-15
Hi!

After seraching google and reading all your posts, finally "imxuk"s solution worked for me!
Thanks and good luck for all the others!

---

### Post by ubergeeknz on 2007-06-27
BTW for you others having problems with evolution/exchange: I found that using https (and not http) improved things a lot, and recently (since some updates) it seems to be quite stable... don't know if that helps anyone.

---

### Post by heliopaixao on 2007-07-17
> **imxuk said:**
> % evolution --force-shutdown
% cd ~/.evolution
% rm -rf `find . -name *exch* -print`

Then restarted evolution, i didnt need to readd my account; although some people report they have had to....

Warning: Before removing any files or directories you should back up your entire ~/.evolution directory just in case something goes wrong and you need to restore it.

The steps above worked to me on Fedora Core 7. Thanks.

---

### Post by gregh on 2007-07-23
I *still* get these problems, sometimes deleting the directory works, sometime not.

It really is not good enough for a corporate environment.

I have tried for years to completely replace MS at work but this one thing *ALWAYS* gives me trouble.
I really hope this can be sorted out sometime soon, it ruins the experience for me (at work).

PS this is not a Ubuntu criticism, just an Evolution one. Maybe now Evolution is supported by novell they have no interest in making it work properly with MS products ?

-Greg

---

### Post by oderus on 2007-09-27
Originally Posted by imxuk  View Post
% evolution --force-shutdown
% cd ~/.evolution
% rm -rf `find . -name *exch* -print`

This did the trick for me. I am running Gutsy Gibbon 64bit with Evolution 2.12.0.

Thanks IMXUK !!!!

---

### Post by wnwek on 2007-10-10
Doing a
```
rm -Rf ~/.evolution
```

did it for me. I didn't need to setup my exchange account again. I am running Feisty 7.04.

---

### Post by jken146 on 2007-11-04
Thank you Imuxk!  This fix worked for me too on 7.10.

---

### Post by bunny rabbit on 2008-01-06
IMXUK's advice worked for me too. Good Times!
Kernel: Linux 2.6.22-14-generic (i686)

---

### Post by tomash_cz on 2008-01-07
Imxuk solution worked for me too!! Great thanks, I have never seen such effective and fast support like open source community!! Thanks again, my exchange in evolution works again and I can finally get back form the W$ and be free again! :guitar:

---

### Post by ramsesdm on 2008-02-01
> **imxuk said:**
> % evolution --force-shutdown
% cd ~/.evolution
% rm -rf `find . -name *exch* -print`

Then restarted evolution, i didnt need to readd my account; although some people report they have had to....

Warning: Before removing any files or directories you should back up your entire ~/.evolution directory just in case something goes wrong and you need to restore it.

it works for me. thanks. i have evolution 2.12 ubuntu gutsy

---

### Post by gunfytr on 2008-02-20
> **imxuk said:**
> % evolution --force-shutdown
% cd ~/.evolution
% rm -rf `find . -name *exch* -print`

Then restarted evolution, i didnt need to readd my account; although some people report they have had to....

Warning: Before removing any files or directories you should back up your entire ~/.evolution directory just in case something goes wrong and you need to restore it.
I'm a linux nubie your post did the trick. Thank you for your fix...

---

### Post by Dr. Falken on 2008-02-21
> **imxuk said:**
> % evolution --force-shutdown
% cd ~/.evolution
% rm -rf `find . -name *exch* -print`

Then restarted evolution, i didnt need to readd my account; although some people report they have had to....

Warning: Before removing any files or directories you should back up your entire ~/.evolution directory just in case something goes wrong and you need to restore it.

it worked for me...

evo 2.12.1@gutsy

---

### Post by DataDaemon on 2008-02-29
Currently all things seem to be working fine for me in Evolution... right up till I hit my calendar.  I have tried the items listed and this has not fixed my issue.  I see one other post about attachments on the calendar causing an issue.... my problem is I ran outlook to VERY recently and thats a lot of attachments.  Anyone else experiencing the same issue and maybe got it resolved??

Thanks

---

### Post by shushu on 2008-03-02
Using the deletion of directories work in a limited amount of time.
After some time the error occur again.

So I guess we still have to wait a stable version from Novell.

---

### Post by superm1 on 2008-03-23
Yup same thing happens to me after using it for a bit still.  Really unfortunate.

---

### Post by will m. on 2008-03-23
I finally gave up on using the Exchange services and persuaded our IT Director to enable IMAP.  Just had to buy him a cup of coffee and a pastry as an incentive : )

---

### Post by superm1 on 2008-03-23
Yeah we have IMAP enabled, but there is no calendar services or name completion on IMAP :(

---

### Post by subru77 on 2008-03-27
I tried the fix. Evolution is still veeeeeeeeeeeeeeerrrrry slow for Microsoft exchange. I am sticking to  it since I love ubuntu.  Can anyone suggest ideas to speedup Evolution? Or can we enable exchange in thunderbird somehow ? 

Thanks

---

### Post by subru77 on 2008-03-27
I still get the message :(

---

### Post by GooblyWoobly on 2008-04-01
This is the single reason I gave up on Evolution. I still use Evolution 2.6.3 on my work PC with an older Fedora Core, and it works fine. They went through a series of breaking and fixing the Exchange support. I guess it's broken again, and broken for some time!!!

I made Kontact/Kmail to work seamlessly with calendaring with Microsoft Exchange. Mail comes over IMAP, Calendaring over WebDAV. The LDAP completion is broken though.
[Link]("http://samya.indiangeek.com/new/blog/2008/02/exchange-server-on-kde-some-ot.html")

 But this is for Kubuntu. GNOME user, hard luck. Maybe Hardy will be better.

---

### Post by superm1 on 2008-04-01
> **GooblyWoobly said:**
> This is the single reason I gave up on Evolution. I still use Evolution 2.6.3 on my work PC with an older Fedora Core, and it works fine. They went through a series of breaking and fixing the Exchange support. I guess it's broken again, and broken for some time!!!

I made Kontact/Kmail to work seamlessly with calendaring with Microsoft Exchange. Mail comes over IMAP, Calendaring over WebDAV. The LDAP completion is broken though.
[Link]("http://samya.indiangeek.com/new/blog/2008/02/exchange-server-on-kde-some-ot.html")

 But this is for Kubuntu. GNOME user, hard luck. Maybe Hardy will be better.
Calendaring over WebDAV?  Any howto on that?  T-bird and lightning are calling my name if I can do calendaring with webdav and imap for mail

---

### Post by GooblyWoobly on 2008-04-01
> **superm1 said:**
> Calendaring over WebDAV?  Any howto on that?  T-bird and lightning are calling my name if I can do calendaring with webdav and imap for mail

Not sure of lightning. There was a writeup on Korganizer here:
[http://wiki.kde.org/tiki-index.php?page=KOrganizer+and+the+MS+Exchange+plug-in]("http://wiki.kde.org/tiki-index.php?page=KOrganizer+and+the+MS+Exchange+plug-in")

---

### Post by xlnc on 2008-05-14
Same problem here with evolution on gusty. stopping the service and removing *exch* files helps thanx! I think it has to do with Archiving. I get the same problem after i have archiving from outlook. At least in my case. cheers!

---

