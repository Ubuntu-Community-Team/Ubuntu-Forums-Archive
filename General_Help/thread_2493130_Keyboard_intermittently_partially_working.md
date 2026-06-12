---
title: "Keyboard intermittently partially working"
date: 2023-12-04
forum: General Help
---

### Post by wforbes on 2023-12-04
Sometimes, the keyboard doesn't work in some apps. Sometimes, it's a browser, next Terminal, etc. Sometimes, unplugging and plugging back in fixes this. Other times, restarting the machine fixes it. Right now, it doesn't work with Firefox/Opera but does with Brave. Terminal works - thankfully. 

This seems like a weird issue. An internet search pulled up an article that mentions autosuspend - or something like that - but the issue here is that it works for some programs and not others and that changes, too.

To be clear, when it doesn't work, it's the case that no keys works, not just certain keys.

---

### Post by TheFu on 2023-12-05
A few ideas.

[LIST]
[*]Try a different keyboard.
[*]Try a different connection into the computer.
[*]If you have a KVM switch involved, remove it.  A logitech keyboard I have hates my KVM switch, but my older, dumber, keyboards don't have any issue.
[*]If you are using a fancy keyboard that usually has drivers under MS-Windows, get a dumb, PS2-connected keyboard.
[/LIST]

Nothing you posted makes me think it is anything other than a keyboard problem.  Does it 100% work if you boot from an Ubuntu Installation Flash drive into "Try Ubuntu" mode?

---

### Post by wforbes on 2023-12-06
Thanks for the reply. 

Yeah, it's a simple USB keyboard. I've tried other inputs with no luck. It's probably just a keyboard problem, as you suggested.

---

### Post by TheFu on 2023-12-06
> **wforbes said:**
> Thanks for the reply. 

Yeah, it's a simple USB keyboard. I've tried other inputs with no luck. It's probably just a keyboard problem, as you suggested.

I have a low-priced Logitech Mechanical keyboard. It is about 11 months old and seems to work.  If I were doing it all again, I'd get a ps2 connected keyboard, not USB.  USB connections take too long when I toggle between different systems, unlike ps2 connections which are instant.  Sadly, the USB-to-PS2 adapters don't work with this "logitech" and the company was less than useless in troubleshooting multiple issues.  They just said, "we don't support that configuration".  Took me 4 attempts until I finally got a CSR to admit they don't test anything odd and that I was on my own.  In 10 yrs when this keyboard dies, I'll avoid that company.  OTOH, this keyboard has an excellent "feel", so far.  I miss the old, old, Norton Keyboard from 1991 that I got by luck. Sadly, it lasted only 1-2 yrs, but it was quiet.  I was using all 100% IBM equipment at work at the time. We had IBM 3278 and 3279 terminals, which were built to last 100 yrs, like the IBM 101M keyboard for PCs.

I've been spoiled. Been using IBM 101M keyboards since the mid-1990s and never expected to need any other.  I started with 3 for $1.50. Gave one a way, thinking I had a spare still.  Then the one stopped working and I swapped in the spare. Used it for 20 yrs and decided to clean it.  That cleaning broke something and I don't have the desire to figure out what broke, but I did keep it since I understand it is worth $150+ when working.  The replacement keyboard has a good "feel" and I don't miss the clickity noise from the IBM at all. There is still some noise, as with all mechanical keyboards. I hate mushy keyboards.

---

### Post by SeijiSensei on 2023-12-06
I've used Logitech wireless keyboards for years. I'm typing on one now. Always been reliable. The keyboard is even available at boot. I tried a Bluetooth keyboard once, but it can't connect until you've logged in so the Bluetooth manager starts. Unless you're a gamer and worry about latency, I'd recommend a Logitech wireless keyboard.

---

### Post by TheFu on 2023-12-06
> **SeijiSensei said:**
> I've used Logitech wireless keyboards for years. I'm typing on one now. Always been reliable. The keyboard is even available at boot. I tried a Bluetooth keyboard once, but it can't connect until you've logged in so the Bluetooth manager starts. Unless you're a gamer and worry about latency, I'd recommend a Logitech wireless keyboard.

If you care about security at all, don't use wireless mice or keyboards.

Around 20 yrs ago, I got a new wireless Logitech mouse and was loving it.  Did some gaming - not FPS, but battle overview stuff - and the battery died at a critical point.  No more mouse and a big chip in the wall. I don't know what happened. I'm fairly mild these days and don't get angry often - may be once a year.  Back then, I had a bit of a problem - especially in traffic.  I stick with corded peripherals ever since.  YMMV. ;)  

Good warning about BT.  Hard to enter storage decryption challenges when no keyboard is working pre-boot.  There are some wireless keyboards with little USB FOBs that hide the wireless aspect of the keyboard.  I've used one of those temporarily when a laptop keyboard died and I needed access to the laptop. ZERO security. Very dangerous to use in compromised areas.

For fun, I've used home-built directional antennas to see what I could capture from neighbors. It was scary, what could be seen.

---

### Post by wforbes on 2023-12-09
I just tried a new keyboard - same problem. The keyboard is only accepting keys in VS Code, not in any other applications. It does work to control the volume, though.

---

### Post by wforbes on 2023-12-13
Thoughts on resetting the BIOS?

---

### Post by wforbes on 2023-12-14
I ran evtest. As usual, typing works in VS Code, Brave but not Terminal.

---

### Post by wforbes on 2023-12-14
After some more searching, I pasted and ran in Terminal

ibus restart

and the keyboard is working again in those apps were just wasn't working. Is this a bug with ibus?

---

### Post by TheFu on 2023-12-14
> **wforbes said:**
> I ran evtest. As usual, typing works in VS Code, Brave but not Terminal.

I'd wonder if VSCode wasn't the problem.

---

### Post by wforbes on 2023-12-14
Every time I have this problem, it always works in VS Code. You think VS Code was causing issues in ibus?

---

### Post by TheFu on 2023-12-14
> **wforbes said:**
> Every time I have this problem, it always works in VS Code. You think VS Code was causing issues in ibus?

That's my theory.

Reboot, don't run VSCode. Does everything work as expected?  
If not, perhaps re-installing ibus, 

Only one of my 20.04 systems has ibus. The other doesn't (not even installed), so it can't really be that important.

---

