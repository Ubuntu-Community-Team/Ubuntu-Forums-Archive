---
title: "Slow and slowing response from Firefox and Chromium after install of 18.04"
date: 2018-05-22
forum: General Help
---

### Post by mynot on 2018-05-22
Have run 14.04 for several years. Saved Home dir. Installed 18.04. Replaced new home dir with old home dir, skipping files with same name. Installed Chromium.

Both Chromium and Firefox slow to contact websites. Videos hang after a few bufferings. Worse when refreshed. After a couple of refreshes hangs with a socket error (whatever that is).

Ran speed test using Telstra Speedtest, which gives good graphical representation. First time gives same result as on other pcs connected to network. Run again - slower. Run again, download is slower than upload. Run again, speed drops smoothly after a few seconds to a few Mb/s (download. Upload is still ok).

I've tried other things like using the installed 18.04 home dir, installing Chromium, and trying again.All gives the same result.

The speed test results sugggest to me a buffer filling up (at a very ignorant guess), but I've no idea where to start to find out what's wrong. All suggestions welcome.

Thanks
Tony

---

### Post by mynot on 2018-05-22
Actually, when the download speed drops off, the upload phase hangs.

---

### Post by jeremy31 on 2018-05-22
If you are using a wifi connection do ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf && systemctl restart network-manager.service
```

---

### Post by mynot on 2018-05-24
Pretty brilliant jeremy31. Don't know what it did but it worked.
Thanks
Tony

---

### Post by bijayalaxmi1808 on 2018-05-24
I did not understand anything even if I read the sed man page.
Could you explain a bit on what the command did, jeremy31, please?

---

### Post by r.vdlee on 2018-05-24
It would have been nice to have a explanation on the commando. It's a good rule of thumb to understand what we run on our desktops. Let me explain this nice one-liner. It consists of two commando's actually. They have been made into a one-liner with the && signs in between these commando's. Read the one-liner like this.

```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

Essential description:
[I]Sed is a stream editor. A stream editor is used to perform basic text transformations on an input stream (a file or input from a pipeline).

[/I]However, in the one-liner above it has been applied --in-place, hence the -i option. Meaning it will replace the line with the regex supplied in the file, also provided. Read the commando like this.

```
sed -i 's/{SEARCHFOR}/{REPLACEWITH}/' /absolute/path/to/file/we/want/to/replace
```

Then there is [Wifi Powersave]("https://docs.ubuntu.com/core/en/stacks/network/network-manager/docs/reference/snap-configuration/wifi-powersave"). It is an option to suspend the wifi radio when not using it to save power. Option 3 is enabled, meaning it will suspend when idle. Option 2 disables this option, meaning it will keep the wifi radio always on. Sometimes this is referred to as "Power mode" on certain operating systems that I will not name here :)

Then after the config has been changed, we need to reload the network-manager to let the config take effect. That is the second command

```
systemctl restart network-manager.service
```

Sources:
[sed man]("https://linux.die.net/man/1/sed") -- for quick reference :)

---

### Post by Holger_Gehrke on 2018-05-24
It's actually two commands; the '&&' is a command separator that only executes the second command if the first one succeeded. The 'sed'-command changes the file /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf (the option -i turns on 'in place editing', normally sed reads a file, executes the commands given either as arguments on the command line or passed as a script file and outputs the result to standard output) and replaces 'wifi.powersave =3' with 'wifi.powersave = 2' (basically this disables power saving for wifi-connections controlled by NetworkManager). If the editing command succeeds, NetworkManager is restarted so it will read the changed configuration.

Edit: [COLOR=#000000]r.vdlee was a bit quicker[/COLOR]

---

### Post by r.vdlee on 2018-05-24
> **Holger_Gehrke said:**
> Edit: [COLOR=#000000]r.vdlee was a bit quicker[/COLOR]

It all comes from a good place, we are both trying to help ;)

---

### Post by mynot on 2018-05-26
Thanks for the elucidation. 

I don't know whether to continue this thread or start a new one, but the problem is not solved as well as I thought.  There are a number of things all connected with the wifi network:
1. Chrome will often (not always) sit on "Resolving host.." or "Waiting for.." messages for maybe 30 secs or more and will sometimes end up deciding there's no connection to the Internet (and then sometimes will promptly go ahead and load the page).
2. Sending email will sit on the "Connecting to server" message for 30 secs or more.
3. The (wifi) printer sometimes takes 30sec or more before receiving the file, and absolutely refuses to print multiple copies - stops after the first. 
Tony

---

### Post by kerry_s on 2018-05-26
> **mynot said:**
> Thanks for the elucidation. 

I don't know whether to continue this thread or start a new one, but the problem is not solved as well as I thought.  There are a number of things all connected with the wifi network:
1. Chrome will often (not always) sit on "Resolving host.." or "Waiting for.." messages for maybe 30 secs or more and will sometimes end up deciding there's no connection to the Internet (and then sometimes will promptly go ahead and load the page).
2. Sending email will sit on the "Connecting to server" message for 30 secs or more.
3. The (wifi) printer sometimes takes 30sec or more before receiving the file, and absolutely refuses to print multiple copies - stops after the first. 
Tony

i think most of that is google having hiccups, there doing something.
when that happens grab another device, phone, tablet, etc... & you'll see the same behaviour.

something's that helped, change your dns severs, i use opendns, try a different search engine.

[ATTACH=CONFIG]279859[/ATTACH]

---

### Post by mynot on 2018-05-26
Thanks kerry_s. None of the other devices on the network were having these problems, but when I changed the dns on this machine to match one of the others it appears that the internet problems are solved. There is still the problem of the printer refusing multiple copies, but that's most likely a different issue. Thanks again.

---

### Post by bijayalaxmi1808 on 2018-05-27
Thanks to r.vdlee for the explanation.

I might be posting not exactly related to the problem but please accept my apologies if I am annoying at times.
I am a beginner and learning as much as I can from the community.

Just curious to know, is it the DNS values are changed after upgrading?
Can this be possible?

---

### Post by mynot on 2018-05-28
bijayalaxmi1808
It was actually a re-install because (I think) an upgrade directly from 14.04 to 18.04 isn't possible.
Tony

---

### Post by mynot on 2018-06-02
I think the problem is associated with my wifi adapter and it's driver so I'll start on a more appropriate thread.

---

