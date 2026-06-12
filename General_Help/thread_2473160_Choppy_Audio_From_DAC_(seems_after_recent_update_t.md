---
title: "Choppy Audio From DAC (seems after recent update this week)"
date: 2022-03-25
forum: General Help
---

### Post by johnsmoke on 2022-03-25
I've had no issues with a USB DAC I've been using for quite a bit now, but just this week I've been having choppy audio with it. I'm wondering if it was because of any updates that I installed to my Ubuntu OS recently this week? Does anyone have any advice or know how I could view updates I've installed this week? Again, only this week did this start, a couple of days ago.

---

### Post by johnsmoke on 2022-03-27
On the line-out "Built In Audio" I don't have these issues. So it's apparently with USB sound devices (my DAC) that this issue is occuring. I've tried all suggestions on this page ([https://unix.stackexchange.com/questions/560545/problem-with-audio-stuttering-choppy-in-every-single-distribution-ive-used](https://unix.stackexchange.com/questions/560545/problem-with-audio-stuttering-choppy-in-every-single-distribution-ive-used)), but none have worked. 

The odd thing is that I had no issues until last week, so I'm wondering if a recent update made this happen? Is there a way to check this? A way to revert my system to a couple weeks ago?

---

### Post by johnsmoke on 2022-03-28
I've deleted and re-added ALSA and Pulse Audio, still no luck. Any advice would be appreciated. It's just so odd that this worked a week ago and now I have audio distortions when listening through a USB dac.

---

### Post by DuckHook on 2022-03-29
My experiences too. I'm afraid my solution will be of limited value to you.

The problem occurred on my new MOBO running Hirsute (21.10). It outputs audio as USB too, rather than the traditional line out. I should note here that the problem also occurred in my USB headphones, so it seemed to be a USB regression of some kind. I worked around the issue by upgrading to the development version of Ubuntu. The problem disappears in Jammy.

I realize this is not a real solution. It ought not to be necessary to risk going to a development version just to get audio. But I personally don't have a better solution to offer you. Jammy works for me because I don't mind the risk, am well backed up, and figured that Jammy stable is less than 4 weeks away anyway so I may as well take the plunge now.

[LIST=1]
[*]Which version and flavour of Ubuntu are you running?
[*]Do the logs tell you anything useful?
[*]Is it all USB outputs or just the main speakers?
[/LIST]

---

### Post by DuckHook on 2022-03-29
A web search found this. I don't know how helpful it really is. Since my audio now works in Jammy, I haven't personally implemented any of the measures within, so please appreciate that you will be doing so at your own risk:

[https://unix.stackexchange.com/questions/560545/problem-with-audio-stuttering-choppy-in-every-single-distribution-ive-used](https://unix.stackexchange.com/questions/560545/problem-with-audio-stuttering-choppy-in-every-single-distribution-ive-used)

---

### Post by johnsmoke on 2022-03-30
> **DuckHook said:**
> My experiences too. I'm afraid my solution will be of limited value to you.

The problem occurred on my new MOBO running Hirsute (21.10). It outputs audio as USB too, rather than the traditional line out. I should note here that the problem also occurred in my USB headphones, so it seemed to be a USB regression of some kind. I worked around the issue by upgrading to the development version of Ubuntu. The problem disappears in Jammy.

I realize this is not a real solution. It ought not to be necessary to risk going to a development version just to get audio. But I personally don't have a better solution to offer you. Jammy works for me because I don't mind the risk, am well backed up, and figured that Jammy stable is less than 4 weeks away anyway so I may as well take the plunge now.

[LIST=1]
[*]Which version and flavour of Ubuntu are you running? 
[*]Do the logs tell you anything useful? 
[*]Is it all USB outputs or just the main speakers? 
[/LIST]


Thanks for your response. Yes, the odd thing is that I had no issues then all of a sudden a week ago I started having problems. It must have been something with an update (kernel, whatever...) that was deployed. I've tried everything else. Deleted sound drivers and re-installed, delete/reinstall PulseAudio. In the link you gave in your next response here, I've tried all those suggestions as well to no avail. The fact that it disappears in Jammy gives me some hope that maybe this will be a temporary issue, so I'll look forward to that once the release is finalized. In response to your questions:

-Running Ubuntu 20.04.04
-how would I obtain the logs I need for this situation?
-I'm trying to use a USB DAC w/headphone & optical ports - any USB port has the same issue, both optical and headphone ports have same issue when outputting sound from the USB DAC

---

### Post by johnsmoke on 2022-04-03
FYI - seems like many are having the issue, due to a kernel update:

[https://bugs.launchpad.net/ubuntu/jammy/+source/linux/+bug/1966066](https://bugs.launchpad.net/ubuntu/jammy/+source/linux/+bug/1966066)
[https://askubuntu.com/questions/1398614/upgrading-to-5-13-0-37-generic-breaks-audio-with-external-audio-card](https://askubuntu.com/questions/1398614/upgrading-to-5-13-0-37-generic-breaks-audio-with-external-audio-card)

I hope this is fixed soon.

---

