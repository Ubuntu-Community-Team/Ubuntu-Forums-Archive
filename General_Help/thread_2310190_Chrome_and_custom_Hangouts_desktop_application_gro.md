---
title: "Chrome and custom Hangouts desktop application grouped. How to ungroup?"
date: 2016-01-16
forum: General Help
---

### Post by Roasted on 2016-01-16
Hello friends. Being a Google Hangouts user comes with certain frustrations with my usage. I don't prefer my hangouts sessions to have to reside in a tab of my web browser simply because I often have so many tabs open. Navigating through my workflow while maintaining a conversation is cumbersome. That said, I got to wondering if I could kind of park my hangout session in my own custom instance of Chrome, so I began tinkering.

I took the chrome.desktop file and named it hangouts.desktop. I downloaded the hangouts icon and set the desktop file to look at this hangouts icon. Success! The other neat thing is Chrome has a launch flag called app, so I can call google-chrome-stable --app=https://hangouts.google.com and it presents me with a Chrome window that doesn't even look like Chrome. No navigation bar, no menu bar, etc. This is not kiosk mode as I can still close the window via the control buttons in the top left.

While I use Firefox predominantly, often times I go into Chrome to edit things. If I have this "Hangouts" instance open and launch Chrome, instead of launching the Chrome icon in my Unity bar, it simply adds a 2nd instance of Chrome under the Hangouts icon. I'm wondering if there's a way I can split that off.

My goal is:

- To have "Hangouts" open, launch Chrome, and Chrome launches in a separate instance from this custom Hangouts setup.
- To have Chrome open, launch "Hangouts", and Hangouts launches in a separate instance from Chrome.

I am basically trying to leverage Chrome, but in its own dedicated isolated environment specifically for Hangouts usage, all while letting my typical Chrome stuff work as it always has.

I looked through the Chrome man page but I didn't see any other flags that might be relevant. Does anybody have any ideas I could try?

EDIT - Running "google-chrome --new-window" explicitly returned this in terminal:
Created new window in existing browser session.

:(

---

### Post by Bucky Ball on 2016-01-17
Have you seen this:

> This isn't quite the same, but the Hangouts Chrome Extension makes it so that you don't need Chrome open to access Hangouts, and also makes for convenient tabs that pop up when someone messages you. I'd suggest checking it out if you want to use Hangouts outside of Gmail and G+: [https://chrome.google.com/webstore/detail/hangouts/nckgahadagoaajjgafhacjanaoiihapd?hl=en](https://chrome.google.com/webstore/detail/hangouts/nckgahadagoaajjgafhacjanaoiihapd?hl=en)

[From here]("https://productforums.google.com/forum/#!topic/hangouts/QY0EeuVYVq0")? Don't know if that's any help ...

---

### Post by Roasted on 2016-01-17
I have seen that, but it wasn't exactly what I was after. I'd really like to find a way to launch Chrome, but force it into its own instance that follows its own icon assigned in the desktop file. The reason being is I have additional uses for an idea like this beyond the Hangouts thought I outlined above. For example, we all know Netflix runs on Chrome. Well, on my HTPC (standard 14.04 install) I have a netflix.desktop application, identical to the hangouts one I explained above however it launches netflix.com in kiosk mode. It makes it feel like an actual app, which is absolutely great for an Ubuntu powered HTPC.

That idea had me wondering... maybe I could spin up a Netflix instance for my laptop too. Only catch is that too stems back to needing to be an independent window of Chrome should I ever be needing Chrome and Netflix at the same time (a common thing actually, as I often do web site work and use chrome to test things yet leave a TV show playing on the other screen).

With these situations, it just kind of suggested that figuring out a way, if at all possible, to leverage Chrome while being split from Chrome would be the best option. Somehow I am doubting that Google graced us with the capability for me to do this... but hey, would rather ask first. ;)

---

