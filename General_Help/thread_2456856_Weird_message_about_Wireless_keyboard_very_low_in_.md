---
title: "Weird message about Wireless keyboard very low in power when changing to tablet mode"
date: 2021-01-20
forum: General Help
---

### Post by emgutierrez on 2021-01-20
[COLOR=#242729][FONT=Arial]I have a laptop Dell Inspiron 7306 2-in-1 with Ubuntu 20.04 LTS. When I convert the laptop to tablet mode and try to use the software keyboard in the touchscreen, Ubuntu sends a notification to the screen saying: Wireless keyboard is very low in power (1%). This device will soon stop functioning if not charged. And suddenly the touch screen just stops responding to user interaction and I have to go back to laptop mode turning back the keyboard to the front.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]On a similar scenario: The laptop comes with a smart pen. When I try to use it without going into tablet mode, the touchscreen does respond to the pen input, but the message about the wireless keyboard with very low power (1%) persists. Also, in Settings->Power->Devices I have the Pen, at 100% and a device called CUST0000:00 04F3:2A2F at 1%, that I supossed is related to the problem.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Additional information: Ubuntu 20.04 Linux kernel 5.8.0-38-generic 64bits.
In PowerStatistic there is a device called keyboard_hid_0018o04F3o2A2Fx0001_battery, that says 
- No suply
- State: Discharging
- Percentage: 1.0%

Thanks![/FONT][/COLOR]

---

### Post by Swan_DB on 2021-01-22
I am just taking an semi-educated guess, but I think it's hardware/Wndows 10 operating system related issue.  And I would hazard a guess that a driver isn't made to make it work how you want.

I did some Googling and that's this is just my best guess, I very well could be wrong though.

Is this your laptop: [https://www.dell.com/en-us/shop/inspiron-2-in-1-laptops/inspiron-13-7306-2-in-1-laptop/spd/inspiron-13-7306-2-in-1-laptop](https://www.dell.com/en-us/shop/inspiron-2-in-1-laptops/inspiron-13-7306-2-in-1-laptop/spd/inspiron-13-7306-2-in-1-laptop)

and here's a discussion about a similar problem with Ubuntu 20.04 on Inspiron laptops: [https://www.dell.com/community/Linux-General/2-in-1-with-ubuntu/m-p/7675955#M17483](https://www.dell.com/community/Linux-General/2-in-1-with-ubuntu/m-p/7675955#M17483)

[B]AGAIN, I am very tired and could be wrong.

[/B]Edit: They appear to be Windows 10 machines, not Linux Ubuntu, so it might take a while for compatibility to start becoming a thing, again, I could be wrong.

---

