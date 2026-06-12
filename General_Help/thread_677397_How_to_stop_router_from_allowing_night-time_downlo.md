---
title: "How to stop router from allowing night-time downloading"
date: 2008-01-24
forum: General Help
---

### Post by FRuMMaGe on 2008-01-24
I want to stop my son downloading things overnight as it is bringing the prices up alot.

How do I use my router to block him IP address to stop downloading after 12 midnight?

---

### Post by p_quarles on 2008-01-24
That would really depend on the type of router you are using, and how fully featured it is/isn't. Details?

---

### Post by FRuMMaGe on 2008-01-24
It's the SpeedTouch 570

---

### Post by p_quarles on 2008-01-24
Well, I had a cursory glance at the manual for that router (available as a .pdf [here]("http://www.speedguide.net/broadband-view.php?hw=68")), and it doesn't look like it supports advanced traffic rules such as the type you're looking for. Short of buying/building a more customizable router, I don't think you can do this. But, like I said, I only took a cursory look at the documentation, so a more thorough look may prove me wrong.

It should be possible to configure your son's computer to do what you're looking for -- but if he has much knowledge about computers, it would be easy him to override any of those settings.

---

### Post by FRuMMaGe on 2008-01-24
> **p_quarles said:**
> Well, I had a cursory glance at the manual for that router (available as a .pdf [here]("http://www.speedguide.net/broadband-view.php?hw=68")), and it doesn't look like it supports advanced traffic rules such as the type you're looking for. Short of buying/building a more customizable router, I don't think you can do this. But, like I said, I only took a cursory look at the documentation, so a more thorough look may prove me wrong.

It should be possible to configure your son's computer to do what you're looking for -- but if he has much knowledge about computers, it would be easy him to override any of those settings.

It has a built in firewall.

Is there a way I could block traffic from his IP address?

Even if it was manually?

---

### Post by p_quarles on 2008-01-24
I'm sure you could manually shut off his access, or block his MAC address, but I don't have the model router, so I can't tell you any better than to look at the configuration page options. Perhaps someone who does have that router will come along, though.

One thought: if he's on wireless, then you could very easily cut him off manually by simply turning off the wireless access point. That should allow any wired connections to continue working, but would disconnect any wireless users. Knowing nothing about your network, obviously, I have no idea if that's practical for you.

---

### Post by FRuMMaGe on 2008-01-24
> **p_quarles said:**
> I'm sure you could manually shut off his access, or block his MAC address, but I don't have the model router, so I can't tell you any better than to look at the configuration page options. Perhaps someone who does have that router will come along, though.

One thought: if he's on wireless, then you could very easily cut him off manually by simply turning off the wireless access point. That should allow any wired connections to continue working, but would disconnect any wireless users. Knowing nothing about your network, obviously, I have no idea if that's practical for you.

You misunderstand.

I still need to use the internet, I just need him to be blocked from it

---

### Post by p_quarles on 2008-01-24
> **FRuMMaGe said:**
> You misunderstand.

I still need to use the internet, I just need him to be blocked from it
I understand the details which you have so far provided, which haven't been very descriptive.

If you're on wireless as well, cutting off all wireless access won't work, as I implied in the last sentence in my previous post. If you were on a wired connection, that would be an option.

Like I said, most basic home routers should have the ability to manually cut off access to a specific computer using its MAC address. Since I don't own this router model, and it's not running a GNU/Linux OS, the best advice *I *can offer is to look at the configuration GUI.

---

### Post by FRuMMaGe on 2008-01-24
> **p_quarles said:**
> I understand the details which you have so far provided, which haven't been very descriptive.

If you're on wireless as well, cutting off all wireless access won't work, as I implied in the last sentence in my previous post. If you were on a wired connection, that would be an option.

Like I said, most basic home routers should have the ability to manually cut off access to a specific computer using its MAC address. Since I don't own this router model, and it's not running a GNU/Linux OS, the best advice *I *can offer is to look at the configuration GUI.

Ok then.

How do I find out the MAC address of my sons computer?

Thanks alot for the help so far by the way :)

---

### Post by PilotJLR on 2008-01-24
Is your sons' computer running Ubuntu? Or Windows?

That will determine how to find the mac address... it will also tell us if using a cron job to shutoff access is an option.

---

### Post by p_quarles on 2008-01-24
> **FRuMMaGe said:**
> Ok then.

How do I find out the MAC address of my sons computer?

Thanks alot for the help so far by the way :)
MAC addresses should show up in the router's listing of connected computers. If for some reason it doesn't, you'd have to get it directly from the computer itself. In Linux, open a terminal and type:
```
ifconfig -a
```
In Windows, open the "Run" dialogue and type:
```
ipconfig/all
```

---

### Post by LaRoza on 2008-01-24
If your son is older than six, he should honor any policy you set. If he breaks it, he shouldn't be using the internet.

---

### Post by FRuMMaGe on 2008-01-24
> **PilotJLR said:**
> Is your sons' computer running Ubuntu? Or Windows?

That will determine how to find the mac address... it will also tell us if using a cron job to shutoff access is an option.

What is a cron job?

Also, he is running Micro$oft Vi$ta

---

### Post by PilotJLR on 2008-01-24
Cron is a linux thing. It's like scheduling tasks... but that doesn't help if he is on vista!

For what it's worth, I know it is possible to schedule an interface to go up, and then down, using Windows task scheduler. Not totally sure of the syntax on Vista / Windows, though... 
It sounds like you are going to do this manually at the router level anyway.

---

### Post by p_quarles on 2008-01-24
> **FRuMMaGe said:**
> What is a cron job?

Also, he is running Micro$oft Vi$ta
A cron job is basically what initially asked about doing from your router: a scheduled command that takes place on a regular basis (e.g., 12 midnight every day).

I'm sure it's possible to schedule something like this on your son's Vista machine, but as long as he has physical access, he can circumvent that. He could also circumvent MAC address blocking, but that would take a bit more knowledge. I think using the router to block his MAC is your best bet at this point, short of getting an enterprise-level router.

---

### Post by FRuMMaGe on 2008-01-24
> **p_quarles said:**
> A cron job is basically what initially asked about doing from your router: a scheduled command that takes place on a regular basis (e.g., 12 midnight every day).

I'm sure it's possible to schedule something like this on your son's Vista machine, but as long as he has physical access, he can circumvent that. He could also circumvent MAC address blocking, but that would take a bit more knowledge. I think using the router to block his MAC is your best bet at this point, short of getting an enterprise-level router.

Ok. I will use the mac filter

---

### Post by FRuMMaGe on 2008-01-24
What about this?

Is there a command here that will let me do this?

[http://www.speedtouch.com/pdf/ST500%20CLI%20Reference%20Guide%20R4.2.pdf]("http://www.speedtouch.com/pdf/ST500%20CLI%20Reference%20Guide%20R4.2.pdf")

---

