---
title: "For a turion laptop, what are normal CPU temp readings?"
date: 2008-03-01
forum: General Help
---

### Post by sloggerkhan on 2008-03-01
So I have a 2ghz single core turion laptop. At least 2.5 or a bit more years old now.
I kinda think maybe it's getting less efficient at cooling, but I'm not sure.
Any case what are acceptable temperature ranges for such a machine?
I think mine only has 2 sensors:
Kernel i2c sensors (hwmon) and ACPI sensor.
I don't know what the difference between these is.
But, ACPI is usually 3-9 degrees C cooler than Kernel i2c.
Kernel i2c seems to run between 50 and 85 C depending on load and use and such.
(When kernel temp says 85, ACPI is 77, but the relationship isn't a direct linear one.)

In any case, I sorta think it's running hotter than it used to, but I don't know how hot it used to run, either. I'm worried because I often do tasks that run my computer at heavy load for extended periods of time, and I also can't really differentiate the dedicated graphics heat contribution from the CPU's.

My concerns are 2:
What if my fans are being controlled by the ACPI temp reading, when the Kernel reading is closer to the actual temp?

Also,  I'm kinda afraid things are running too hot. As an example, 704x480 mkv file with ffh264 encode and vorbis audio  makes my system run at a constant 84/85 degrees C according to Kernel i2c....

More explicitly, I'm kinda worried that either my cpu or my graphics card might be overheating occasionally....

---

### Post by metallicamaster3 on 2008-03-01
Somewhere around 50-55 degrees Celsius. Anything  about 60 should give you caution.

---

### Post by sloggerkhan on 2008-03-01
hmm. I was sorta thinking along the same lines. 60 degrees was going to be my thought...
But yeah, I guess my comp is definately running too hot.
50-55 is like its idle temp.

---

### Post by wolfen69 on 2008-03-01
sounds like a hardware issue. maybe a fan isnt working as it should.

---

### Post by sloggerkhan on 2008-03-01
That's possible. However, the system does seem to be stable through 85 degrees.... It's just that that seems rather hot. But yeah, maybe there's a small internal fan or something that's dead I don't know about.

---

### Post by sloggerkhan on 2008-03-01
So I looked up what I could, and it sounds as though I'm lucky to have computer that runs stably at 85 degress C, lol.

I took it apart and cleaned what I could, and without putting the top  panel back on, it idles at 39 C now, and seems to only get up to high 60s C.  Still, it might be time to think about a new computer. I don't know. I accidentally ruined the keyboard taking it apart. :(

---

### Post by sloggerkhan on 2008-03-03
Edit: Apparently some turions are able to run stably at up to 90 C, though I couldn't find anything explicit about my CPU.

The fact that it idled at about 40 C new and now idles at 37 C case open, whereas it was idling near 60 C after use before and now only gets there under load convinces me that there was some sort of cooling problem.

---

