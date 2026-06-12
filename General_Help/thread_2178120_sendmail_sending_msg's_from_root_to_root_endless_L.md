---
title: "sendmail sending msg's from root to root endless Loop"
date: 2013-10-02
forum: General Help
---

### Post by David_Macdonald on 2013-10-02
Ok So i'm very inexperienced in all this, I am at a unmanaged host a friend recommended.

He installed everything for me, Ver 12.04 x64

To allow my script to send mail via php he installed send mail and we tried to send out a mass email back on 9-30 the system killed it after a while. We had it set to send 100 every 10 sec in the script. it send some msg's to the Root user saying that it was using to much resources more then 200mb of virtual ram i think is what it said. then I guess something happened and Localhost.com started timing out and deferring the msg's ATM there is over 80,000+ msg's in the Queue from [email]root@mydomain.com[/email] to [email]root@mydomain.com[/email] saying that Local host timed out as stated above. This number is getting larger by the Second and the amount of CPU and HDD use it going up along with it.

I haven't got the Slightest Idea what to do to fix this.

As far as I've seen poking around what he did was use Googles dns servers in the resolver.conf and there SMTP to send the emails since email is not installed on the server. He has gone MIA and i'm afraid that its going to keep growing tell it takes up all the HDD space and cause the server to crash. It should be noted that emails are going out when you reset passwords and such. What i think is happening is them msg's from the other day saying it was using to much resources and that something killed it after only a few min's of sending are bouncing back and forth and each time it times out it creates a new one saying it timed out in a loop over and over.

Also the Email for the domain (smtp) is being hosted on a different server.

Root inbox accessed via webmin
[http://prntscr.com/1ur3al](http://prntscr.com/1ur3al)

After Clicking one of the MSG's sent (only about 300 some came though before the Loop started, no more since have came in I have even deleted some just in case there was a limit set on number of mails or size and not more have came in just loops)
[http://prntscr.com/1ur3e8](http://prntscr.com/1ur3e8)

MSG's in the Cue
[http://prntscr.com/1ur3on](http://prntscr.com/1ur3on)

After Clicking one
[http://prntscr.com/1ur3r0](http://prntscr.com/1ur3r0)

The CPU and HDD use where going UP and UP so i Restarted send mail via Webhosting admin and it Changed the Pattern of usage.
[http://prntscr.com/1ur464](http://prntscr.com/1ur464)

I have access to Console so if there is things you need me to look up and such to help me I can.
I'm at a lose as to what to do and want someone to just hit me in the head with a 2x4
This is driving me nuts.
I Told him about what was going on and his response was Interesting... But your site is sending emails fine so...
Not being very helpful then went offline.

Thank you,
David M.

---

### Post by David_Macdonald on 2013-10-02
No one has any Idea why this is happening or how to stop it?

:cry:

---

