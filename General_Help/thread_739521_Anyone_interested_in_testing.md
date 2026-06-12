---
title: "Anyone interested in testing?"
date: 2008-03-29
forum: General Help
---

### Post by aitvo on 2008-03-29
I've been working on a way to connect to my iPaq automatically when I log in, and I've created a package out of the udev scripts. I've tested these on two computers and they seem to work great, so here's the how-to:

First, disconnect your iPaq if it's connected.

Next, install the ipaq-udev-scripts from my repository [[LINK]("http://public.stangdude.com/pool/main/i/ipaq-udev-scripts/ipaq-udev-scripts_1.0.3_i386.deb")]. 

While you can just install that one package, I recommend apt-get installing it from my repository because there are several dependencies that will need to be installed first that apt will fetch.

If you aren't interested in that, cool here are the dependencies (not all of them are required but I've required them by the deb because they are small and I figured I'd cast a large net).

*synce-dccm, synce-multisync-plugin, synce-serial, libmultisync-plugin-all, multisync, multisync-tools, librra0-tools*

Once you have the ipaq-udev-scripts package and it's dependencies installed, add "dccm" to your user profile.

Click System -> Preferences -> Sessions.
Click the "Add" button, then enter DCCM for the name.
Type "dccm" in the command textbox without the quotes, and give it a comment if you want. Click the "OK" button then the "Close" button.

Now; either log out and back in or alternately press ALT-F2 and type "dccm" in the textbox without the quotes and click "Run". You won't get any notification that dccm is running, but that's OK.

When you've gotten past this part, open a terminal and plug in your iPaq. You can get to the terminal by clicking Applications -> Terminal. In the terminal, type "synce-matchmaker create INDEX" and you should get a response that it's been created. If not, try turning off your firewall first then repeating this part (disconnect the iPaq, and start this paragraph over).

That's pretty much it, now you can use multisync to sync your Pocket PC with whatever you want, and when you boot the computer my udev scripts will connect to the device as soon as you log in.

---

### Post by aitvo on 2008-04-01
bump

---

