---
title: "Sometimes no login screen since 4.18.0-14"
date: 2019-02-09
forum: General Help
---

### Post by 2CV67 on 2019-02-09
Hi!

I have been using the same hardware since 2014 (then with Ubuntu 14.04).
I upgraded through each Ubuntu version, getting 18.10 with 4.18.0-13.14 on 16 Jan, with no problem.

On 7 Feb I installed updated kernel 4.18.0-14.15.
It booted OK (confirmed by uname -r) first time.
But next boot, I ended up with a black screen instead of login screen.
I got out with REISUO.

Selecting 4.18.0-13 at the grub screen showed that the earlier kernel still booted OK.
Confirmed several times.

Trying to boot to 4.18.0-14 seems to have about a 50% success rate.
When things go OK, I pass through:
- Acer splash screen
- Grub screen
- "No signal" notice
- Ubuntu splash screen with spots sequencing
- Login screen

When things go wrong, I get as far as just seeing the Ubuntu splash screen for a second, then nothing.
No mouse pointer.
I can always escape with REISUO.

I assumed there must be a problem in 4.18.0-14 & decided to just wait for the next kernel.
Today I installed 4.18.0-15.16 but it has the same behaviour as 4.18.0-14.

Thanks for any help or suggestions!

---

