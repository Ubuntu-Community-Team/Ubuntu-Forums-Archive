---
title: "Phone for use with Ubuntu"
date: 2014-07-30
forum: General Help
---

### Post by Keith_Beef on 2014-07-30
After several years of great service my Nokia XM5800 is beginning to behave somewhat flakily and is showing its age.

Here are examples of what's wrong.
[LIST]
[*]Not setting the clock to network time. When I took a trip back to the UK a short while ago, I bought a T-Mobile SIM card to use and discovered that the phone's clock would not set itself to the local time (even though the phone went off-network, came back on, and displayed a message that it was fetching the local time). On arriving back in France I put my Free SIM card back in, and discovered the same problem. So it was not a T-Mobile problem, it is a phone problem.
[*]There are very few apps being developed for Symbian.
[*]The screen is a bit scratched, so handwriting is sometimes not accurately recognised.
[*]The dictionary app is limited to three languages at a time (when it should have been developed to allow as many languages as the memory can take).
[*]The phone firmware is limited to handling a subset of European languages.
[*]Nokia's own web browser is limited (Opera in my experience is unstable on this platform) and connecting to WiFi networks is sometimes flaky.
[*]The GPS receiver seems sensitive enough, but the software is very slow to calculate a position. Even when I get strong signals from seven satellites, I need to wait for up to fifteen minutes to get my position!
[*]The killers:
[LIST]
[*]There's no way to sync to my Ubuntu computers in order to keep track of my calendar, to store text messages, to store contacts. When I was working, I used to keep my phone in sync with my work computer running Outlook; this took care of alerts for meetings and I could let colleagues know what they needed to know through a shared calendar. For example if I was in the kPCR lab from 08h30 to 10h30 then in conference room B until noon, my colleagues could see that. I could have an alarm to warn me of a meeting starting in 30 minutes,  giving me time to scrub up and walk from the lab to the meeting. The calendar and alerts in the phone being synched with Outlook was an *extremely* useful feature.
[*]There's no reliable way of downloading new maps to my phone. Nokia wants me to use a Windows program to manage my phone and install new maps. They're free of charge, and once or twice I've been able to get to a server to download maps to my computer, mount the phone as an external drive and copy the files, but that door seems to be closed, now. Same goes for the limited number of apps: if I can download a SIS file, I can copy it to the phone and install it, but Nokia prefers to lock me into using the Windows program. This is not an option for me. 
[/LIST]
[/LIST]

Here are examples of what's great about this phone.
[LIST]
[*]It's a nice size and shape, I've seen people struggling to hold or pocket some horribly huge devices that look like phone/tablet hybrids. I'd like something a similar size, just a slightly bigger screen.
[*]On-board maps and navigation! No need for an expensive data plan to use GPS. (But see the gripe about slowness, above.)
[*]Quite a good music player. The built-in speakers are tiny, but sound good for their size; output to wired headphones or through BlueTooth to headphones or speakers is great.
[*]A good video player, either on its own (smallish) screen or through the special cable to a TV set.
[/LIST]

So, now for my list of requirements for a new phone.

[LIST]
[*]A recent version of Android.
[*]Synchronisation of text messages, calendar entries and contacts with my Ubuntu computers and also with my future employers' computers (almost certainly Windows, probably with Outlook but possibly Lotus Notes or something I've never heard of).
[*]Multilingual: I need to able to write in many languages and many writing systems. I mostly use English, French, German, Russian and Greek; I cannot accept having to install language support packs for subsets of languages just for a day, half day, or hour of work. I would also prefer to be able to use East Asian languages as well: especially Korean but Vietnamese, Japanese (at least hirogana and katakana) and Chinese would be useful
[*]Fairly good camera with flash: I use my Nokia's camera to take notes, especially during disassembly / reassembly procedures. I don't need super-high resolution (3 MPixels is enough).
[*]Dictionary app that is limited only by available memory.
[*]Expandable memory: through at least one micro SDHC or SDXC Card slot.
[*]The phone must, absolutely, charge through a USB connector. I think that this is an EU requirement, but I expect manufacturers will be given some time before compliance is enforced. I'm not prepared to accept proprietary or round-style charging connectors any more.
[/LIST]

Now for secondary considerations&#8230; things that would be nice, but which are not absolute deal-breakers.
[LIST]
[*]I don't need a ridiculously huge battery; most of the time the GPS and BlueTooth can be switched off, and I'm in the habit of carrying a spare phone battery or an external booster battery for situations where I know I won't be able to recharge the phone.
[*]I don't need a huge or super hi-res screen, just being bright enough to read in strong sunlight would be great.
[*]Being waterproof or bulletproof would be fantastic, but not essential. Water "resistant" should be enough; i.e., I should be able to use it in the rain!
[*]Dual-SIM would be nice, so that I don't have to take out my French SIM card when I travel to another country, or so that I can have a personal SIM and a work SIM.
[/LIST]

I know that some people will tell me to just go into a phone store and ask for advice, but in my experience the people in there are absolutely clueless when it comes to anything out of the ordinary and are in any case more interested in selling the most expensive device with the most expensive data plan.

And I know that some people, even here on UbuntuForums, will seriously propose installing Windows as a guest in a virtual machine, or setting up a dual boot Windows/Ubuntu system, but I am not prepared to buy a Windows license simply to get one or two features (synchronisation of my phone with the computer, for example) that I believe should be available already.

I'm perfectly prepared to install some middle-ware or server between Lightning and Thunderbird and the phone. After reading the threads I could find on my dilemma, I think that Radicale might do the job. I am NOT prepared to send all my calendar and contacts through a cloud or other online service in order to get them from phone to computer or vice-versa.

So, anybody got any pearls of wisdom to throw my way? 



(p.s. I expect that this will get transferred to "Forum: Recurring Discussions".)

---

### Post by Irihapeti on 2014-07-30
I can't comment on which phone would do the job for you. I do know that you can sync calendar and contacts to Ubuntu without needing to run a VM or a cloud service. Radicale works well to sync calendar and contacts, in conjunction with Davdroid.

---

### Post by Keith_Beef on 2014-07-30
> **Irihapeti said:**
> I can't comment on which phone would do the job for you. I do know that you can sync calendar and contacts to Ubuntu without needing to run a VM or a cloud service. Radicale works well to sync calendar and contacts, in conjunction with Davdroid.

Thanks for the info. I saw some of your responses in the other threads, and was hoping you'd give me some advice.

So if I've understood: I would run Radicale on the computer, DAVdroid on the phone. 

One thing on the DAVdroid page concerns me, though: 
> two-way-synchronization (server &#8596; client, server always wins)

Maybe I have misunderstood… "server always wins" looks to me like whenever I make a change to calendar or contacts and then sync, the server's version is used to update the phone, wiping out the changes I had made.

---

### Post by Irihapeti on 2014-07-30
I'm not quite sure what they mean by "server always wins". I do know that I've made changes on the phone and they've synced successfully back to the server. Possibly, server wins if you've changed an item on both server and phone before syncing - but I do my best to avoid that sort of thing.

One strange thing I've noted: if I create or change an item on the phone, it ends up marked as "tentative" in Lightning and shows up sort of greyed out. I don't know what causes it, but as it's easy to change in Lightning, I don't worry about it.

---

