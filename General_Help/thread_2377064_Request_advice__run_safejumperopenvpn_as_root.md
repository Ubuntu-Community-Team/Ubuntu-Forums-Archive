---
title: "Request advice:  run safejumper/openvpn as root?"
date: 2017-11-08
forum: General Help
---

### Post by m9ke2 on 2017-11-08
Running Ubuntu Mate 16.04 and SafeJumper openvpn client build 79.  Just upgraded to SafeJumper client build 79.

Upon attempting to connect I get a message I have not seen before on earlier SafeJumper builds:
```
Authentication is needed to run /opt/safejumper/launchopenvpn as the super user.
```
I have authenticated as root and run SafeJumper, and it connects without issues.

But---I am leery of running this app as root.

I go to /opt/safejumper/launchopenvpn, and inspect the properties and permissions for launchopenvpn.  It's an executable.
Owner is root, Group is root.  The 'Allow executing the file as a program' check box is checked.

The Properties box informs me that I am not the owner, so I cannot change these permissions, and they are greyed to indicate that.

Seems like I have 2 choices, and I would request advice on which is more secure:
Choice 1:  authenticate as root every time I connect via the vpn
Choice 2:  change the permissions for launchopenvpn such that I have permission to run launchopenvpn as myself, not root.

Could I hear from folks about which choice (1 or 2) is more secure, or perhaps another solution i haven't thought of?

Thanks!

---

### Post by DuckHook on 2017-11-08
I would have great misgivings running a VPN client as root. I use PIA and it is not necessary to run its client as root.

Just what are the permissions of the safejumper executable? You state that it's owned by root, but is it universally executable? Though I am unfamiliar with safejumper, please post results of:```
ls -lh /opt/safejumper/launchopenvpn
```

---

### Post by m9ke2 on 2017-11-09
Thanks for your reply, DuckHook!

```
-rwxrwxrwx 1 root root 4.7M Aug 22 15:11 /opt/safejumper/launchopenvpn
```

---

### Post by DuckHook on 2017-11-09
Have you asked safejumper about this? Either on their forums or their customer service?

---

### Post by m9ke2 on 2017-11-09
Previous builds of safejumper do not require a root authentication.  I upgraded to the then-latest build months ago, got the request to run openvpn as root on my first launch.  I promptly reverted to an older build, and filed a support ticket.  On 04/26/17 they said:

> [COLOR=#737373][FONT=Lato]In the next 2 to 3 weeks, we will work hard to implement a change to Safejumper to make it work as a system service, so it won't require the root anymore.[/FONT][/COLOR]
[COLOR=#737373][FONT=Lato]I have extended your service for free by an extra month as a courtesy. Please wait for the next software update and keep us updated on how it goes.[/FONT][/COLOR]

It was nice of them to extend my service, and I have been running an older build since then  But months later build 79 (the latest) still requires a root auth to launch openvpn.

Reason I am revisiting this is the old build will no longer run on my system, which I keep updated pretty diligently.

I know it's insecure to run openvpn as root.  It's hard to think that all the users of the latest build are running openvpn as root.  Like you, I am extremely skeptical about that!

What I don't know is the correct permissions for launchopenvpn at /opt/safejumper/launchopenvpn

Maybe solving this is as simple as changing the permissions for launchopenvpn to myself.  But maybe changing those permissions is as insecure as running openvpn as root.  

What do you think?

---

### Post by DuckHook on 2017-11-09
After some further reflection, running your VPN client as root may not be that big a deal. It depends whether you trust this VPN provider and whether the code is reliable. And if we don't trust our VPN provider, then why are we funnelling all of our traffic through them in the first place, right? As for the code, many people run closed-source video drivers without worries.

My VPN provider is PIA and their client runs in userspace, not root. In fact, it is installed under my /home directory and not /opt. However, the code is just as closed-source. Moreover, if an app is rogue, it doesn't need root access to do its dirty work. A keylogger, for example, will work quite nicely in userspace without root.

If you still don't like the idea of an opaque app running under root (many people use Linux precisely because they don't), then look for instructions from your VPN provider to set up VPN access via Network Manager's native VPN options instead of using the safejumper client app.

I don't advise changing permissions for your VPN client app, and most definitely not by taking ownership of the file. Your client app was installed in /opt for a reason and probably uses some system extensions or libraries to work. Changing ownerships might break the app and possibly your system too. It might be possible to do this through some tuning of sudoers, but this would just open a hole in your sudo profile. If the goal is tightened security, then this would be a case of the cure being worse than the malady.

---

### Post by m9ke2 on 2017-11-10
Thanks, DuckHook for your thoughtful reply.

Yep, I don't much like running as root, nor do I like changing permissions, which as you pointed out are the way they are for reasons.

I think something is not quite right in the way i set up the vpn.  I will work with the provider to straighten it out.

Thanks again for your thoughts DuckHook!

---

