---
title: "Weird website login behavior only on Ubuntu"
date: 2024-10-30
forum: General Help
---

### Post by uacnt83982803 on 2024-10-30
This problem just started occurring.  Logging into statefarm.com (using Brave browser).  Enter UN and PW, next step is to select either a text or email for a security code.  I select one or the other, retrieve it, enter it, then the problem starts.

In rapid order, the URL in the browser switches between statefarm.com, auth.proofing.statefarm.com, and apps.statefarm.com.  And repeats this cycle quickly and endlessly.

This problem does not occur on a Windows PC, nor does it occur on my Android phone.

To solve the problem on my Ubuntu PC, I have taken the following steps:
[LIST=1]
[*]Cleared cookies and cache - no change, same symptoms occur
[*]Turned off all Brave shields - for each of the 3 URLs that it cycles through - no change, same symptoms occur
[*]Tried Firefox - no change, same symptoms occur
[*]Removed Brave software and reinstalled - no change, same symptoms occur
[*]Installed ungoogled Chromium - no change, same symptoms occur
[*]Restarted PC again and retried Brave - no change, same symptoms occur
[/LIST]

At this point, I am led to conclude that this is some sort of Ubuntu issue.  Is this possible?

One final note - after closing Brave, then reopening it and going to the state farm website, the 3-URL cycle start repeating again as soon as I click the Log In button on the main page.  In other words, this authentication cycle is still going somehow in the background.

---

### Post by yancek on 2024-10-30
>  At this point, I am led to conclude that this is some sort of Ubuntu issue.  Is this possible?


Before you can realistically come to that conclusion, I would think you would need to verify that behavior is the same at other sites requiring login and password.  Have you done that?  Do you happen to have another 'live' Linux OS (not Ubuntu or derivative) on a usb to try the same test?

Maybe someone else who uses that site will post but I doubt many members will be interested in logging in there just to test.

---

### Post by uacnt83982803 on 2024-10-30
This problem only exists (that I've seen) on this particular website.  I have never had a similar problem on other websites.  I don't easily have the ability to test on another Linux system though I could probably boot Ubuntu on another PC and test it that way.

I did contact the site's IT support and a ticket has been put in.  Strange though that on Brave, Firefox, and Ungoogled Chromium this behavior exhibits itself (on a Ubuntu machine) but I don't have the issue at all on Windows or Android, both using Brave.

---

### Post by yancek on 2024-10-30
>  I don't easily have the ability to test on another Linux system though I  could probably boot Ubuntu on another PC and test it that way.

Why would you do that if you believe the problem is with Ubuntu?  You have an internet connection so you could go to distrowatch and download an iso of another NON ubuntu Linux, write it to a usb, boot it and go to the site to test.  If it fails also, then it less likely it is Ubuntu.  If it does not fail, that is some evidence there is something in Ubuntu.  Have you changed the user agent in the brave or firefox browsers to show it is running windows?  There is some discussion of this at the brave web site so you might do a search there.  The link below is one such thread.

[https://community.brave.com/t/configure-user-agent/88719/7](https://community.brave.com/t/configure-user-agent/88719/7)

Based on your last post, it is more likely that it is something about the web site.  You can easily find sites discussing user agent switching for firefox.

---

### Post by uacnt83982803 on 2024-10-31
The issue turns out to have been the time change that Ubuntu initiated one week earlier than it should have, in the US.  Once I deleted my time zone data and reset it, the website issue went away.

[https://askubuntu.com/questions/1531298/ubuntu-22-04-changed-out-of-daylight-savings-time-one-week-early](https://askubuntu.com/questions/1531298/ubuntu-22-04-changed-out-of-daylight-savings-time-one-week-early)

---

