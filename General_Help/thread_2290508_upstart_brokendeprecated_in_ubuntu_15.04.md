---
title: "upstart broken/deprecated in ubuntu 15.04?"
date: 2015-08-12
forum: General Help
---

### Post by roland-logikalsolutions on 2015-08-12
Weird problem with desktop versions. Perhaps upstart has been deprecated and I simply haven't seen the documentation, but...

I have a remove-myapp.conf file. It is a one time conf file to remove a demonstration application. Under Ubuntu 14 32&64 bit raw installs I can copy the .conf file to /etc/init (without ever installing the demonstration app) and type:

sudo start remove-myapp

everything is perfect.

Under raw installs of Ubuntu 15.04 both 32&64-bit the same test yields the following error:

start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused

These are raw installs from the desktop ISO.

Is there a different way for me to test this with Ubuntu 15.04 or is this legitimately broken?

Thanks,

---

### Post by deadflowr on 2015-08-12
> [COLOR=#000000]Weird problem with desktop versions. Perhaps upstart has been deprecated and I simply haven't seen the documentation,[/COLOR]
This.
You must not have read the [Release Notes for 15.04]("https://wiki.ubuntu.com/VividVervet/ReleaseNotes"), but Ubuntu now defaults to Systemd.
(Upstart, if i recall correctly can be loaded if chosen from the grub boot menu. There should be an option for in in the advanced options section)
I'd suggest reading the linked [SystemdForUpstartuUsers]("https://wiki.ubuntu.com/SystemdForUpstartUsers") page.

---

### Post by roland-logikalsolutions on 2015-08-13
> **deadflowr said:**
> This.
You must not have read the [Release Notes for 15.04]("https://wiki.ubuntu.com/VividVervet/ReleaseNotes"), but Ubuntu now defaults to Systemd.
(Upstart, if i recall correctly can be loaded if chosen from the grub boot menu. There should be an option for in in the advanced options section)
I'd suggest reading the linked [SystemdForUpstartuUsers]("https://wiki.ubuntu.com/SystemdForUpstartUsers") page.

Thanks, I'll give it a read. I must say sweeping changes like this make it difficult to develop things which work release to release. It's one of the reasons Ubuntu is a non-player in the server market. There stability always trumps "cool this week."

---

### Post by grahammechanical on 2015-08-13
> It's one of the reasons Ubuntu is a non-player in the server market.

You are years out of date with that observation. You also miss the point. Ubuntu is built on Debian and it was the Debian developers that stopped using Canonical's Upstart as an init system and switched instead to Redhat's SystemD. By deciding to accept what was coming from Debian Ubuntu developers avoided getting involved in someone else's argument. And apparently there was quite an argument among Debian developers over the switch.

---

### Post by Frogs Hair on 2015-08-13
Derivatives of these distributions would be using systemd as well.

---

### Post by roland-logikalsolutions on 2015-08-17
> **Frogs Hair said:**
> Derivatives of these distributions would be using systemd as well.

While the list is pretty, it neither proves nor disproves anything. I personally don't care one way or the other which is used. The issue, and I suspect vast amount of the heat in the debate, comes from consistency & stability. The RPM based distros in that list had systemd before the Debian switch and they still had it after. The debian based had Upstart, then, suddenly didn't. It's an "abandon the installed base" kind of thing, at least for the places which had upstart jobs. When providing a .deb package which needs to make use of starting at user login it now must provide both the Upstart stuff it had for pre-Ubuntu 15 and now systemd stuff.

Having just ported Upstart stuff to systemd I have to say, systemd is bunches and bunches cleaner. Very well thought out.

---

### Post by Frogs Hair on 2015-08-17
> While the list is pretty, it neither proves nor disproves anything.  The list is not intended to prove anything it's just an FYI. ;)

---

### Post by ian-weisser on 2015-08-17
> **roland-logikalsolutions said:**
> I must say sweeping changes like this make it difficult to develop things which work release to release. It's one of the reasons Ubuntu is a non-player in the server market. There stability always trumps "cool this week."

That's one reason why 12.04 LTS and 14.04 LTS (most popular for production servers) have not changed. 16.04 LTS will, of course, use systemd.

The systemd transition in 15.04 (much less popular for servers) was thoroughly announced, discussed, and tracked in many developer venues, community venues (incidentally including many, many threads in this forum), and in the release announcements and release notes.

Many of us tried really hard to communicate the change. Sorry you missed all our efforts.
Please feel free to suggest a communication method or channel that would work better for you and others next time.

The contributing members of the Ubuntu community are proud of it's versatility, stability, usability, and security. Sorry that you don't see what we're proud of.
Please feel free to join the contributor and/or testing communities and help us achieve a better Ubuntu.

---

### Post by roland-logikalsolutions on 2015-08-17
> **ian-weisser said:**
> That's one reason why 12.04 LTS and 14.04 LTS (most popular for production servers) have not changed. 16.04 LTS will, of course, use systemd.

The systemd transition in 15.04 (much less popular for servers) was thoroughly announced, discussed, and tracked in many developer venues, community venues (incidentally including many, many threads in this forum), and in the release announcements and release notes.

Many of us tried really hard to communicate the change. Sorry you missed all our efforts.
Please feel free to suggest a communication method or channel that would work better for you and others next time.

The contributing members of the Ubuntu community are proud of it's versatility, stability, usability, and security. Sorry that you don't see what we're proud of.
Please feel free to join the contributor and/or testing communities and help us achieve a better Ubuntu.

One of the problems with Linux distros in general is the focus of communication. The focus is always on new communication, not cleaning up the old stuff. The old stuff tends to rank higher in search engines. I'm typing on a new laptop right now so please forgive any horrible typing. Do a Google search for "Ubuntu run script at startup" and the first link which turns up is: [http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up](http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up) there are many more links all talking about using Upstart. None of them has been edited to include some note indicating this only works in versions prior to 15.04.

Yes, there probably was an ocean of communication and people may have worked hard at it, but the old stuff gets left laying around to become a landmine. As I stated, this is not a problem unique to Ubuntu, but it is a growing problem. At some point in the near future each Linux distro is going to have to admit it has become a heritage system. With that moniker comes the burden of cleaning up the old stuff. The old stuff will have higher search engine rankings so will cause massive frustration for people trying to adopt. With this particular change I would humbly suggest someone be tasked with cleaning up as much of the old stuff as can be found prior to 16.04 coming out.

A similar problem also exists with preseed files. A preseed file which adds the sudo user complete with password, never showing the Ubiquity screen to enter a user which worked with 14 does not work with 15.04. It fills in the username, machine name, and user-fullname, but password values are ignored, causing the screen to appear with two empty password fields. I posted a question about this on here a few days ago and it has been met with deafening silence. I spent today digging through the Ubiquity code and from what I can find the same same syntax for providing passwords "should" work, but they don't. Before logging out today I found a script on some site in a foreign language which claims to work with 15.04. I cannot be certain because I don't read that language so I can read the code, but not the explanation. They may very well be telling me it doesn't work. Kickstart files are also ignored, which, I guess is okay since system-config-kickstart will not run on 15 and will only run on 14 after replacing the hardware package from Debian. I haven't found a hardware package which makes it run on 15.04 and I suspect, that is also why the ks.cfg is being ignored.

Another link which turns up in the search for running jobs at startup is [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto) which also doesn't mention the change to systemd with 15. Ubuntu 11 seems to be the last time it was touched. True, there are a good many links which show up that are not under the Umbrella of Ubuntu, but, some reasonable effort should be made at getting the owners of the sites to flag/remove/edit the posts to stem the tide of misinformation. 

That is just my 0.0002 cents worth on the matter.

---

### Post by ian-weisser on 2015-08-17
> **roland-logikalsolutions said:**
> With that moniker comes the burden of cleaning up the old stuff. [...] With this particular change I would humbly suggest someone be tasked with cleaning up as much of the old stuff as can be found prior to 16.04 coming out.

I think you have highlighted a well-known, recurring problem.
Many attempts have been made to address stale documentation: Different organizations, systems, and technologies have been repeatedly tried over the past 10 years in Ubuntu.
It's still an unsolved problem.

Good documentation writers and editors are rare and often under-appreciated when they do their volunteer job well.
The pages I have edited and updated were tedious and thankless tasks. So I stopped, and moved on to more rewarding contributions.

---

### Post by roland-logikalsolutions on 2015-08-18
> **ian-weisser said:**
> I think you have highlighted a well-known, recurring problem.
Many attempts have been made to address stale documentation: Different organizations, systems, and technologies have been repeatedly tried over the past 10 years in Ubuntu.
It's still an unsolved problem.

Good documentation writers and editors are rare and often under-appreciated when they do their volunteer job well.
The pages I have edited and updated were tedious and thankless tasks. So I stopped, and moved on to more rewarding contributions.

This is the primary reason serious companies stick with pricier computing options. Back in the day of the VAX, before Alpha and Itanium when OpenVMS was called VMS, the doc set was referred to as "The Orange Wall." Newbies wanting to know something were told to "pray at the orange wall." Documentation came in orange 3 ring binders and was measured in shelf feet. I never worked at a place which had the full set. Various rumors circled as to the total shelf feet required. The most I ever saw for a single version set was 36 shelf feet and that was not the full set. One place had both PDP and VAX equipment with multiple versions of the OS. They had close to a dozen 6 shelf book cases back to back all in a room. The documentation was maintained by paid professionals and proofed by VMS engineering before it or the OS version was released. I'm sure the same is true for IBM's various operating systems as well. 

Accurate documentation created by professionals separates commercially viable operating systems (meaning safe to base your business on) from the hobby platforms. I have not looked at Oracle's Linux offering, but, given the mountain of documentation they produce for every other product I would be shocked to learn they weren't already clearing mountains in Oregon to generate the rough drafts.

Yes, I know what an effort it is to create professional grade documentation: [http://theminimumyouneedtoknow.com/](http://theminimumyouneedtoknow.com/)
There is only one book in that series which I donated to an OpenSource project and that was for the xBaseJ library. I don't work in Java anymore, but, at the time I was and needed to use the library. The "documentation" consisted of 3, or 4, tiny, barely commented example programs. That was it. Unlike most in the OpenSource community I decided if I was going to have to read the code to find out what it did, I was going to write it down. The thing has been posted in more places than I can count. About half a dozen people seem to be claiming it as their own on Scribd.

The "script kiddies" doing much of the OpenSource development have yet to work on professional products in a professional environment. The types of systems which need to stay in place and be supported for 20-30+ years. I was once young too. Back then it was called shareware and had to be distributed via BBS hops.

The Linux distro which will ultimately win the paid server market is the one which comes with complete and accurate documentation both on-line and in Web format.

---

