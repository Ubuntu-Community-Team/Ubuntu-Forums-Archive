---
title: "Can't format PC after installing Ubuntu 13.10"
date: 2014-02-22
forum: General Help
---

### Post by Profetak on 2014-02-22
Ubuntu 13.10 is not running well (I guess I played around too much). Now I need to format my computer and reinstall the operating system. 
But when I reboot with the installation CD inside, nothing happens (I've tried with different CDs and even with a bootable USB stick). There is no message, no option on the screen like there was before I installed Ubuntu 13.10! Now it goes straight to Ubuntu. As soon as I reboot, I try to press all possible keys as far as I know: all F* keys (F1, F2... F12), tab, esc, del, shift. 

I've already formated this computer dozens of times in the past and is was always so easy, this had never happened. I don't know if the problem is with ubuntu or if i changed some option in the Bios on the last installation.

Some help, please!!!

---

### Post by Profetak on 2014-02-22
SOLVED!

Somebody told me I would have to reset the bios. To do that it's necessary to disconnect the PC, open the CPU [I mean, system case], remove the battery, wait for a couple of minutes, put the battery in place again, reconnect the computer and turn it on. The first thing you should see is the option screen telling you which keys you should press for configuration. This was the screen that had disappeared, that's why I wasn't able to access the installation CD to format. But now it's solved!

---

### Post by Topsiho on 2014-02-23
> **Profetak said:**
> SOLVED!

Somebody told me I would have to reset the bios. To do that it's necessary to disconnect the PC, open the CPU, remove the battery, wait for a couple of minutes, put the battery in place again, reconnect the computer and turn it on. The first thing you should see is the option screen telling you which keys you should press for configuration. This was the screen that had disappeared, that's why I wasn't able to access the installation CD to format. But now it's solved!

I am at a loss what you mean with: open the CPU. Do you mean opening the system box?

Just to prevent readers to remove their CPU's when trying this advise themselves :)
And I 've never had to reset the BIOS (changed the boot order) this very cumbersome way. Never even have touched this battery.

Topsiho

---

### Post by Profetak on 2014-02-24
In Portuguese (my native language), we use CPU to refer to this big box (system box, that's what you say). I just typed CPU in google images and lots of these big boxes I refer to appeared. I thought we'd refer to the same thing in English. Anyway, whenever I turned on the computer, Ubuntu would open first thing, without giving me the chance to access the BIOS setup. So somebody told me I'd have to reset the BIOS by removing the battery inside the system box for a couple of minutes. I don't know if there is an easier way to reset the BIOS, but anyway, it solved my problem! :)

This is the battery I'm talking about (it looks like a coin):
[http://www.laercio.com.br/faqs/2000/2000_13.jpg](http://www.laercio.com.br/faqs/2000/2000_13.jpg)

---

### Post by Topsiho on 2014-02-25
I just can't believe that in Portuguese (a language foreign to me) CPU is used as you say. Maybe some Portuguese do, but then do it wrongly. CPU is an abbreviation of Central Processing Unit, also known as the processor. It's the ==> chip <== within a computer that does all (well, almost all, some are often done in the graphics card) the calculations and processing.

See: [http://www.webopedia.com/TERM/C/CPU.html;](http://www.webopedia.com/TERM/C/CPU.html;) [http://www.newegg.com/CPUs-Processors/Category/ID-34;](http://www.newegg.com/CPUs-Processors/Category/ID-34;) [http://pcsupport.about.com/od/componentprofiles/p/p_cpu.htm;](http://pcsupport.about.com/od/componentprofiles/p/p_cpu.htm;) and so on, all found googleing on "CPU"

What I called the system box most often is called the system case, English is not my native language :)

I don't know, maybe someone else can help us here: if when booting the system boots into Ubuntu immediately, then you should press some (which one?) key on the keyboard when starting the computer, to get to the screen that lets you to press Del, or F1, or whatever, to get into the BIOS setting menu. Sometimes you have to press F12 to boot from USB.

I never have this problem as on my computers I have set the booting order to first CD-Rom, and then HD. When booting, first the CD-Rom is checked for the presence of a bootable CD-Rom or DVD-Rom, and if there isn't, then the computer starts from the HD.

Topsiho

---

### Post by Topsiho on 2014-02-25
I have looked at CPU in googleimages, as you did, and indeed some of the images are system cases. That doesn't mean that CPU's are system cases. There is also an image of a pair of military pants there, and a screen that you get when you type top in a terminal. A lot of nonsense. Many more images are clearly not CPU images.

:)

Topsiho

---

### Post by Profetak on 2014-02-26
Well, natural languages are not "logical" - what makes sense in a language is just the conventional way people use. There are many cases of words from a specific language that acquire a different meaning in another. In Portuguese we have examples of words that are from English, but have a different meaning, or are not used the same way. For example, to refer to a "USB flash drive", everybody in Portuguese says "pendrive". I just discovered it was different from English because when I used the word "pendrive" to talk to a British friend, she didn't understand what I was talking about! 

Take a look at this picture, it indicates the parts of a computer in Portuguese, showing what I mean by "CPU":
[http://3.bp.blogspot.com/-fL102CiOQjM/Teec6lxVRcI/AAAAAAAAABg/8JaScRPVwCk/s1600/escreva+os+nomes+das+partes+do+computador+5%C2%BAano.JPG](http://3.bp.blogspot.com/-fL102CiOQjM/Teec6lxVRcI/AAAAAAAAABg/8JaScRPVwCk/s1600/escreva+os+nomes+das+partes+do+computador+5%C2%BAano.JPG)

Besides, if you type "CPU" in a Brazilian online store, you'll see pictures of them selling "system cases".
See this advertisement about a "CPU" from Casas Bahia (one of the biggest stores in Brazil):
[http://www.youtube.com/watch?v=g7ICP9vmYmc](http://www.youtube.com/watch?v=g7ICP9vmYmc)

Anyway, I just remembered we also use the word "gabinete" in Portuguese.

---

### Post by Impavidus on 2014-02-27
Google checks your IP address. If it's portuguese or brazilian, it will show images of what's called a CPU in portuguese, if it's dutch, in will try and find images of what's called a CPU in dutch or images from dutch websites. Indeed, mostly processors. It's not very reliable though, but it explains why people get different results.

As an example, [this site]("http://www.grymoire.com/Unix/Sed.html") says it's the number 1 page on google for searches for sed (valuable resource, by the way). In the Netherlands it isn't, as the first page belongs to a restaurant in 's Gravenmoer (Samen Eten en Drinken=Eat and Drink Together). And it doesn't say it's a sponsored link.

---

