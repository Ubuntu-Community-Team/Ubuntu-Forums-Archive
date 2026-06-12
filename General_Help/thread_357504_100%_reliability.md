---
title: "100% reliability"
date: 2007-02-09
forum: General Help
---

### Post by Rich78 on 2007-02-09
If you wanted a 100% reliable Ubuntu workstation (Desktop), which version would you go for?

6.06?

If so why?

---

### Post by taurus on 2007-02-09
Because Dapper, 6.06, is a LTS--Long Term Support.

---

### Post by Rich78 on 2007-02-09
OK so it has long term support, but does that make it a more stable release?

---

### Post by taurus on 2007-02-09
If you look around here, you would see that more people have success running Dapper on their machines than Edgy but it's up to you if you want to install Dapper or Edgy.  Personally, I don't have any problem at all on two of my machines running Edgy.

---

### Post by ~LoKe on 2007-02-09
> **Rich78 said:**
> OK so it has long term support, but does that make it a more stable release?

A release that's LTS is the most stable release, because it's the one that will be officially supported for so long.  They wouldn't support a release that long if there were stability problems; too much work required.

---

### Post by teaker1s on 2007-02-09
my experience is it all depends on your hardware, I have a two dapper installs=perfect
A laptop that is unuseable on Dapper or Edgy but good on feisty.
motto of this is old hardware= good new=poor support

---

### Post by Rich78 on 2007-02-09
OK cool, I'm not doubting it but I'm wanting to decide what would be best for a business server and desktops.

I run Edgy currently and generally have no problems but every now and again something might bomb out, usually Firefox and it can sometimes do weird things like one instance all the desktop icons disappeared.

Now on Windows I'd expect that sort of thing but Linux has always had more of a stable reputation.

Admittedly the machine this happened on had no updates at the time, so maybe it's been fixed but I just didn't expect it.

My other problem which has brought about this discussion is that I'm currently setting up NIS on a client machine (I've already done this for one client and server successfully, this will be the second client on the network).

I installed NIS and configured it to point to the domain.
I then added the server to my hosts.allow config.
I then proceeded to hookup the various services to map to NIS.

I got as far as /etc/shadow and when I vi'd it to edit the file it took forever to load it up, so I got impatient and quit the terminal as it wouldn't ctrl c out of it.

I then tried to edit the file again and it did the same.

I then logged out, which took for ever and then tried to log back in, this also sat on the password screen for ages, so before it logged in I chose to shut the PC down via the shutdown option on the login screen.

When I booted back up, it took an age again to get to the login screen, I then logged in, which sat on the password screen again but I decided to sit it out.

I then had a problem loading up Gnome and is now sat on the default Gnome theme, which may rectify after a reboot, but it's still running like a dog to vi any config files.

This has started to make me question the stability of it for business use.

---

### Post by r4ik on 2007-02-09
Not trying to be a wise*** here but it's the users contribution witch increases stability.

---

### Post by Rich78 on 2007-02-09
I understand what you're saying but basic networking should be possible without it spitting it's dummy.

I don't want to be in a situation where by I replace a whole business setup for Ubuntu only to find it  gives me more grief than Windows does (if that's possible).

---

### Post by teaker1s on 2007-02-09
buy compatible hardware that has been out forever and dapper=no problems

---

### Post by Rich78 on 2007-02-09
Just to add to my comments, after letting it do it's thing and finishing off the config, after a restart of the NIS service and a reboot everything seems back to normal.

*Edit: Except I get an error saying "Failed to initialize HAL", any ideas?

Thanks

Obviously my main question is still applicable from a business decision perspective and whilst I'm not expecting people to make my mind up for me, I'm just wanting some opinions of others more experienced then me.

---

### Post by r4ik on 2007-02-09
> **Rich78 said:**
> I understand what you're saying but basic networking should be possible without it spitting it's dummy.

I don't want to be in a situation where by I replace a whole business setup for Ubuntu only to find it  gives me more grief than Windows does (if that's possible).

I agree absolutely,and it was not personally.
Some people do have the habit to kick a distro around though and then complain if it breaks :)

---

### Post by Rich78 on 2007-02-09
Same goes for many Windows users, they install loads of junk and then wonder why it breaks, admittedly they could probably use it with installing loads of junk and Windows will install the junk for you and still break, but you know what i mean ;).

If I was mucking about with bleeding edge stuff then yes I agree it would be my fault for the instability, but I have to trust any updates prompted are to be installed?  and NIS is pretty old technology.

I guess I just really like Edgy compared to Dapper, I don't know what it is, it just seems a bit slicker, but I don't want that to get in the way of reliability.

I've found a for the HAL problem, turns out many on here have had that one!!

---

### Post by r4ik on 2007-02-09
If you want stable,and a bit boring,try Debian.
For Ubuntu i would say use LTS.

Good luck !

---

### Post by 23meg on 2007-02-09
Dapper has had a 1.5 month extra bug fix period added to the usual six month schedule. It's not the most stable version of Ubuntu in absolutely everyone's experience, but the fact that no other release has had a dedicated bug fix period and the fact that it's the release Canonical is most confident with (hence their extra log support of it) should give you an idea.

---

