---
title: "Yahoo.com Videos Don't Work"
date: 2014-04-18
forum: General Help
---

### Post by Smallwheels on 2014-04-18
Yahoo.com is where I go often because I have a Yahoo mail address. I peruse their news and entertainment stories. On many of their pages are video news clips and other videos. On many of their pages the videos won't play. They just give me an error message. At first I thought this was a Firefox problem. Then I went to the same pages with Chrome and got the same results. I had this problem with 13.10 and now on 12.04 LTS. I switched to it temporarily due to other problems. I'll use it until 14.04 is running well. 

These videos are viewable on my 2008 Mac Book that is running a very old version of Firefox and the OS X 10.5.8 Leopard OS. Is anybody else experiencing this? What could be going on?

I have the restricted extras package and I can play DVDs on my system, if that information helps. 

[https://screen.yahoo.com/viral-hits/sneaky-dog-vandalizes-cars-6-232504866.html](https://screen.yahoo.com/viral-hits/sneaky-dog-vandalizes-cars-6-232504866.html)

---

### Post by squakie on 2014-04-18
i'll be watching this as I started getting this exact thing when I went to 14.04 beta.  I have suspected it's a message they dump out when they check the flash version and it isn't what they deem new enough.   However, I could be way off on that ;)

---

### Post by carl4926 on 2014-04-18
It's working here in openSUSE 13.1 Chrome but not firefox
I'll check 14.04 later when I switch machines

---

### Post by carl4926 on 2014-04-18
> **carl4926 said:**
> It's working here in openSUSE 13.1 Chrome but not firefox
I'll check 14.04 later when I switch machines
Chromium works too, but that's with the pepper flash

---

### Post by monkeybrain20122 on 2014-04-18
It works on Chrome and firefox with pipelight-flash  but not firefox with system flash so I suppose it doesn't like flash 11.2

---

### Post by squakie on 2014-04-19
That's what I was thinking when I made my post - it's checking the flash version, wants one higher than what we can get for Linux, so instead of the "update needed" message other sites post using the imbedded player,  I think they are just kicking out this "Ooooppsss" some error has occurred message.

I'm curious - is this "pepper flash" available for Ubuntu, or is it only a chrome thing?  Also - pipelight - I tried this before but never had any luck.  Are there things I need to remove/purge prior to installing it?

---

### Post by carl4926 on 2014-04-19
14.04 firefox - no
chromium with pepper - yes

Pepper flash is avail for chromium in 14.04
or just install chrome, where it is built in

---

### Post by Smallwheels on 2014-04-24
How do I get pepper flash into Firefox and Chrome? I've gone to Mozilla and the Google App Store and searched for extensions and plug-ins. All I find are programs that block Flash or allow Flash videos to be downloaded.

---

### Post by monkeybrain20122 on 2014-04-24
You can't get pepper flash in Firefox. It is bundled with Chrome so you just need to install Chrome.

---

### Post by QDR06VV9 on 2014-04-24
For Trusty 
```
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```
For saucy
```
sudo add-apt-repository ppa:skunk/pepper-flash
sudo apt-get update
sudo apt-get install pepflashplugin-installer
```
Then after it installs 
```
echo ". /usr/lib/pepflashplugin-installer/pepflashplayer.sh" | sudo tee -a /etc/chromium-browser/default
```

---

### Post by monkeybrain20122 on 2014-04-24
> **runrickus said:**
> For Trusty 
```
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```
For saucy
```
sudo add-apt-repository ppa:skunk/pepper-flash
sudo apt-get update
sudo apt-get install pepflashplugin-installer
```
Then after it installs 
```
echo ". /usr/lib/pepflashplugin-installer/pepflashplayer.sh" | sudo tee -a /etc/chromium-browser/default
```

These are for Chromium. OP asked about Firefox and Chrome. With Firefox it won't work, with Chrome you won't need it (already bundled)

---

### Post by QDR06VV9 on 2014-04-24
> **monkeybrain20122 said:**
> These are for Chromium. OP asked about Firefox and Chrome. With Firefox it won't work, with Chrome you won't need it (already bundled)
Options that's all more than one way to skin a cat.
Maybe some else will find it useful if that's alright with you.
And I do not, like many others here use Chrome but Prefer Chromium

---

### Post by Smallwheels on 2014-04-24
Thank you folks for being so quick with those answers. For now I'm using 12.04. Will either of those instruction sets work in that version?

I'm waiting for the dust to settle before jumping in with 14.04 LTS.

---

### Post by Frogs Hair on 2014-04-24
I wonder if it is a flash problem or  something  Yahoo related ? I can watch Bing Video and Vevo via Youtube ,but I can't watch Vevo via Yahoo in Firefox .

---

### Post by squakie on 2014-04-25
> **Frogs Hair said:**
> I wonder if it is a flash problem or  something  Yahoo related ? I can watch Bing Video and Vevo via Youtube ,but I can't watch Vevo via Yahoo in Firefox .

See my first post in this thread......  I believe it's Yahoo looking for a certain flash level or higher, not finding it, then rather than dump out the typical "update your flash player" they instead dump out the Ooopppss message.

---

### Post by Smallwheels on 2014-05-01
I used the commands for Saucy Salamander just to see if it would work for 12.04. I tried it in Chrome. The video did play. That was good. I selected a video using Firefox and it didn't work.  My favorite browser is still Firefox because there are some plug-ins I like that don't function as well in Chrome. I really want to get Yahoo videos working in Firefox. How do I do that?

If there is no simple way to do it I'll just use Chrome for most of my browsing and turn on Firefox when I need those special plug-ins. I find that the Video Download Helper works best on Firefox. I use it to save TV shows for better viewing. Streaming on my computer in full screen isn't as reliable and smooth as recording the videos and using VLC to play them. Chrome just doesn't utilize Video Download Helper to the same degree. I also don't find the same level of pop-up blockers and ad-blockers. I use Do Not Track Me, Ad Block Plus, and sometimes I want to use Right to Click.

---

