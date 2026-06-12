---
title: "Flickering Screens with Dual Monitors"
date: 2016-05-14
forum: General Help
---

### Post by colmurp on 2016-05-14
Im familiar with *nix but I have a problem , I have two Asus external monitors , one is connected via HDMI and the other is connected via VGA ( these are the only ports available to me ) 

I was able to get both screens working from my laptop , however when I upgraded to 16.04 the mouse is causing a flickering black box on the screen it exits.  This box is always at the height of the mouse.

I have attached the terminal output from **xrandr **and some information about the graphics card 

could anybody offer advice ? thanks

---

### Post by DuckHook on 2016-05-14
Hi and welcome to the forums, colmurp.

I'm afraid your HW info is incomplete. Can't tell from the screenshot what your GPU specs are.

Instead of Perl, please do a simple:```
lspci -vn | grep -iA13 vga
```...and just post the text output back to this thread. The xrandr output is fine as is.

You have a lot going on in your system. I'm surprised that your little Intel graphics chip can drive three displays, and two of them at relatively high resolutions too (even if the laptop display is dormant). You mention that you didn't have this problem until you upgraded to 16.04. What did you upgrade from? Were you using proprietary drivers previously?

I've also moved your thread into General Help which is more in line with your problem and where a user who can use Perl really belongs. ;)

---

### Post by colmurp on 2016-05-14
thank you for moving my thread to the correct location, I have upgraded from 14.04, here is the output from the command you offered. I am not sure if I was using the proprietary drivers previously , I dont think that I was was as I enabled them for this issue. I know that my graphics card is weak but If it was able to drive two external monitors on a previous LTE it should be able for 16.04

---

### Post by DuckHook on 2016-05-15
> **colmurp said:**
> ...I know that my graphics card is weak but If it was able to drive two external monitors on a previous LTE it should be able for 16.04This is a very reasonable expectation, but unfortunately, it is often not achievable. Xenial has not yet reached its first point release and there are still plenty of bugs to be worked out in its implementation. Ubuntu/Linux veterans will delay LTS-to-LTS upgrades until the first point release (16.04.1) for exactly this reason. Also, the kernel devs have a big quandary: they have to get rid of old drivers to make way for new ones. Otherwise, the kernel would bloat into an impractical size. This will sometimes leave very old peripherals behind. While yours obviously still works, it may by subject to a regression that makes it less stable than the last LTS.

I see the following options:
[LIST=1]
[*]
[*]You go back to 14.04. Many users don't like this option but it is, in fact, a very viable one. Your Trusty install gave you no trouble, all the functionality you needed and is supported until 2019.
[*]
[*]You install a flavour that is less taxing on your GPU like Lubuntu, Xubuntu or Ubuntu-Mate (I never understood why it isn't just called Mubuntu). Since your artifact may be the result of overtaxing your rendering engine, a lighter flavour could make it go away.
[*]
[*]If the artifact is not too distracting, you live with it until the first point release comes out and see if that doesn't solve the problem 16.04.1 will probably be out in another 3 months time.
[*]
[*]We try a few kernel parameters that may destabilize your system altogether, or give you a black screen, but have low probability of success. These parameters are usually used to offload processing from the GPU to the CPU, or to invoke power-saving, or to fix specifically known faults with certain cards, i.e. pretty drastic surgery. Since your artifacts don't fall into such nothing-to-lose territory, you would be squashing a bug with a wrecking ball, so to speak.
[/LIST]
I would frankly recommend #1. I'm still using it on my servers and other boxes in which stability and reliability are my primary objectives. I feel that too many users jump on the shiny new pony when their old warhorse is still hale and healthy. You can try 16.04.1 in a LiveUSB session after it comes out, and install it only if the artifact problem has been solved.

---

