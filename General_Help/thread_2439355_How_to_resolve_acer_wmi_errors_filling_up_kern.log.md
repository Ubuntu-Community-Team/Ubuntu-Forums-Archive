---
title: "How to resolve acer_wmi errors filling up kern.log and syslog?"
date: 2020-03-26
forum: General Help
---

### Post by monojamoon on 2020-03-26
[COLOR=#242729][FONT=Arial]Recently bought an Acer Predator Helios 300 and was able to create a working Ubuntu 18.04 and Windows dual boot setup in my third attempt.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I really have my doubts whether all the modules have integrated successfully, hence, I keep an eye out for recurring errors in syslog and kern.log. And currently, both the files are being cluttered with the following message:

```

[FONT=Consolas]acer_wmi: Unknown function number - 11 - 0[/FONT]

```

They occur every minute. The exact logs look like this:

```

[FONT=Consolas]Mar 25 06:52:37 rand_user667 kernel: [ 1095.786969] acer_wmi: Unknown function number - 11 - 0[/FONT][/FONT][/COLOR]
Mar 25 06:53:28 rand_user667 kernel: [ 1146.197270] acer_wmi: Unknown function number - 11 - 0
Mar 25 06:54:18 rand_user667 kernel: [ 1196.610322] acer_wmi: Unknown function number - 11 - 0
Mar 25 06:55:08 rand_user667 kernel: [ 1247.024422] acer_wmi: Unknown function number - 11 - 0
Mar 25 06:55:57 rand_user667 kernel: [ 1295.635244] acer_wmi: Unknown function number - 11 - 0
Mar 25 06:56:47 rand_user667 kernel: [ 1346.046235] acer_wmi: Unknown function number - 11 - 0
Mar 25 06:57:38 rand_user667 kernel: [ 1396.452391] acer_wmi: Unknown function number - 11 - 0
Mar 25 06:58:28 rand_user667 kernel: [ 1446.860010] acer_wmi: Unknown function number - 11 - 0
Mar 25 06:59:19 rand_user667 kernel: [ 1497.276243] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:00:07 rand_user667 kernel: [ 1545.880528] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:00:59 rand_user667 kernel: [ 1598.088886] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:01:48 rand_user667 kernel: [ 1646.698326] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:02:38 rand_user667 kernel: [ 1697.102227] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:03:29 rand_user667 kernel: [ 1747.510677] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:04:19 rand_user667 kernel: [ 1797.919387] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:05:08 rand_user667 kernel: [ 1846.332304] acer_wmi: Unknown function number - 9 - 1
Mar 25 07:05:08 rand_user667 kernel: [ 1846.536522] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:05:58 rand_user667 kernel: [ 1896.952896] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:06:49 rand_user667 kernel: [ 1947.381534] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:07:39 rand_user667 kernel: [ 1997.789819] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:08:30 rand_user667 kernel: [ 2048.195628] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:09:20 rand_user667 kernel: [ 2098.595164] acer_wmi: Unknown function number - 11 - 0
Mar 25 07:10:10 rand_user667 kernel: [ 2148.993292] acer_wmi: Unknown function number - 11 - 0 
[COLOR=#242729][FONT=Arial][FONT=Consolas]Mar 25 07:11:01 rand_user667 kernel: [ 2199.383051] acer_wmi: Unknown function number - 11 - 0[/FONT][/FONT][/COLOR][COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
```
[COLOR=#242729][FONT=Arial]
Did some Googling around to find out that acer_wmi is a helper module. And most of the posts related to acer_wmi ultimately leads to blacklisting of the module. However, all of them had a non-functioning WiFi and they blocked acer_wmi to resolve that issue. The Wifi on my computer is working fine (although the connection seems to be a little slow).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I stumbled upon [this post]("https://askubuntu.com/questions/922140/how-to-know-i-have-to-blacklist-acer-wmi?rq=1") which talks about the necessity of blocking acer_wmi. I followed the steps, did a rfkill list all :

[/FONT][/COLOR]
```

1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```


[COLOR=#242729][FONT=Arial]None of them are blocked.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Next command was lsmod | grep acer_wmi:

[/FONT][/COLOR]
```

acer_wmi               24576  0
sparse_keymap          16384  1 acer_wmi
wmi                    32768  3 intel_wmi_thunderbolt,acer_wmi,wmi_bmof
video                  49152  2 acer_wmi,i915

```


[COLOR=#242729][FONT=Arial]I don't understand the output at all. But my guess is it lists the services that are attached with acer_wmi. In the [aforementioned URL]("https://askubuntu.com/questions/922140/how-to-know-i-have-to-blacklist-acer-wmi?rq=1"), there are two modules attached to sparse_keymap. So blacklisting acer_wmi from my computer will quite likely disable sparse_keymap?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is blocking acer_wmi the solution to cluttering of the logs? What should I do? Please advice.


[/FONT][/COLOR]

---

