---
title: "Problem installing Ubuntu / Xubuntu"
date: 2006-11-04
forum: General Help
---

### Post by Bou on 2006-11-04
Hi guys, let's see if you can give me a hand with a problem I'm having here:

I've tried to install Ubuntu in an old desktop my girlfriend has inherited from her parents (they're perfectly healthy, they've just given it to her because they didn't use it anymore), which has about 300 ghz and 64mb RAM.

I figured it wouldn't be able to run Ubuntu, but I tried just in case. It can't indeed, I get this error message after the usplash:

> ACPI: UNABLE TO LOCATE RSDP

So I tried Xubuntu instead, but I get more or less the same issue: After getting the usplash, the screen turns black with just an underscore blinking at the top left corner.

Can you give me a hand? I don't want to have to install W98!!

---

### Post by jimbob on 2006-11-04
Not sure what stage of the install process where this is happening.

Since it is related to ACPI can you try adding 'noacpi' and 'acpi=off' on the kernel boot line? (Without the tick marks).

If not you might try doing a text mode install from the alternate CD to see more closely where it is happening.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by dermotti on 2006-11-04
acpi=off vga=771

---

### Post by Bou on 2006-11-05
> **dermotti said:**
> acpi=off vga=771

Nope, it won't work. A blank screen replaces the ACPI error message.

In Xubuntu I get the same exact behaviour as before.

---

### Post by bjoernw on 2006-11-22
i've got the same problem with my old laptop these days.
it finally worked with the xubuntu **alternate install** cd (text mode).
so this may be worth a try... :-D

in addition you could search the bios for some acpi functions not activated yet...

---

### Post by MyMistake on 2006-12-05
Did you ever get this resolved? I've got the same thing happening. I downloaded and burned 6.06 and when I boot up with it on my old Dell Inspiron 1100, it starts out okay. I get a screen asking what I want to do and when I say install Ubuntu, I get the perpetual blinking underscore.

Thanks!

---

### Post by jimbob on 2006-12-06
Was this with the alternate CD using the text mode install?

If not, give that a try.

---

### Post by Bou on 2006-12-07
> **MyMistake said:**
> Did you ever get this resolved?

Not really, I could give the text installer a try I guess...

Do you think xubuntu would work fine with a 300 mhz computer with 64mb RAM?

---

### Post by Sgood1971 on 2006-12-07
> **Bou said:**
> Not really, I could give the text installer a try I guess...

Do you think xubuntu would work fine with a 300 mhz computer with 64mb RAM?

I have it running on a 200mhz with 128MB RAM, slow as can be but functional.

---

