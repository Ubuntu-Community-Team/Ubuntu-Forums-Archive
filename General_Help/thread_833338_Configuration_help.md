---
title: "Configuration help"
date: 2008-06-18
forum: General Help
---

### Post by will_hoaccio on 2008-06-18
I recently had to "old-yeller" my mom's computer. As I am extremely cheap, I bought the cheapest computer parts I could and now to avoid the thing running like a snail w/vista, I need to configure Hardy to do 3 things.


Basically they are:

1.)Easy usability. My mom doesn't know what a "sudo" is and she doesn't want to know. Any settings or additions that could make Ubuntu simpler for her, the better. Text interface is not an option.

2.)Quick load times. It won't be expected to do much beyond very basic things (firefox, mahjong, word processing, bit torrent), but it has to do those fast.

3.)Reliability. I cannot stress how important this is. If I get a call in the middle of a lecture about something linux related not working, I will kill Mark Shuttleworth.I need programs that are proven and reliable. 

If it is important, the computer is a Core 2 E7200 2.53 Ghz, 2gb DDR2, Asus 8500GT, 320gb Seagate HDD and an ASROCK mobo. 

What applications should I have or not have? What is the best WM or DE? Is Ubuntu even the right distro for this? Any help in how I could configure this to get the best balance of those three goals would be greatly appreciated.

---

### Post by prshah on 2008-06-18
> **will_hoaccio said:**
> 
1.)Easy usability. 
2.)Quick load times.
3.)Reliability.

If it is important, the computer is a Core 2 E7200 2.53 Ghz, 2gb DDR2, Asus 8500GT, 320gb Seagate HDD and an ASROCK mobo. 


With these specs, ubuntu will do swimmingly. I'm more than a little surprised Vista is slow on such a machine.

(3) is easy to achieve, especially with someone who doesn't know and doesn't want to know what sudo is. (1) and (2) depend more on the initial setup, which, once locked down, will not lend themselves to change.

I'd also suggest you use Kubuntu which will have a more familiar ;) ;) interface. Further, I'd suggest you set up 2 users, one with admin privileges and one "restricted" user, so that she'd not be bothered by updates. You should also setup OpenSSH and remote admin capabilities so that you needn't be physically at her computer to fix problems (except for Internet problems!) and for maybe once-a-week updates. [EDIT] Also setup auto-login [EDIT]

And in case there are problems, I hope you'll make sure it's not hardware or PICNIC (Problem In Chair[user], Not In Computer) before you go hunting with an elephant gun.

---

### Post by sdennie on 2008-06-18
Ubuntu is actually a great distro for people that don't know how to use computers well.  Because those people didn't understand Windows well, the learning curve is not very steep when moving to Ubuntu.  What I usually do when setting up an Ubuntu computer for someone like that is to install it and then personally open and configure every app the person is likely to use to save them the confusion of doing so.  After that, I just show them Add/Remove Programs and the update manager and tell them that apart from logging in, those are the only times it's safe to enter their login password.

---

### Post by pytheas22 on 2008-06-18
I second what's already been said...Ubuntu is great for people who don't know much about computers and need an operating system that will do one basic thing reliably for a long time.  I've had my family on Ubuntu for over a year now, and everything they use runs exactly the same as it did when I first set up the machine.  Their accounts are locked down, so they can't screw anything up, and I no longer have to worry about malware taking control of the computer.  This is important because I'm only around for a couple months every year; other than that they're on their own.

The one place where we have run into issues is Internet applications that don't want to cooperate with Linux.  Turbotax is an example; for some obscure and sketchy reason, it refuses to work if it detects Linux, even though I don't see why it makes a difference.  Some websites that stream video do the same thing.  Because of this, I set up the Windows version of Firefox in wine and tell the family that if something on the Internet ever fails to work using the normal Firefox, they should use the alternative one (I put an icon on the desktop and label it ALTERNATIVE FIREFOX to avoid confusion).  I also set up a virtual machine running Windows XP for extreme problems, but that hasn't yet been necessary.

And I also second the importance of setting up ssh or vnc as a way for you to administer the computer remotely when necessary; this has saved me lots of trouble.  Make sure you set strong passwords for these services to thwart brute-force attacks.

---

