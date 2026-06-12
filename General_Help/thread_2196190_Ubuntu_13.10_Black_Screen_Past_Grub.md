---
title: "Ubuntu 13.10 Black Screen Past Grub"
date: 2013-12-28
forum: General Help
---

### Post by ogdencam on 2013-12-28
[COLOR=#333333][FONT=UbuntuRegular]I've had Ubuntu 13.10 installed for a couple of weeks. It has ran smoothly the whole time. Starting today, whenever I try to boot into Ubuntu, I'll view Grub and the the [/FONT][/COLOR][Splash Screen]("http://www.thefanclub.co.za/sites/default/files/styles/300-wide/public/images/howto/ubuntu-boot-splash.png?itok=9AT2L2e9")[COLOR=#333333][FONT=UbuntuRegular] loads and then [/FONT][/COLOR][a black screen with a constant underscore]("http://www.servethehome.com/wp-content/uploads/2013/10/Cursor-Blinking-Screen-600x333.jpg")[COLOR=#333333][FONT=UbuntuRegular] shows, after that, nothing happens. Trying to boot using nomodeset will start a command line (no GUI). Running [/FONT][/COLOR]startx[COLOR=#333333][FONT=UbuntuRegular] will fail; the only noticeable feature is that it says "(EE) No Screens Detected." Trying to disable Secure Boot and enable "Launch CSM" yields identical results. My computer is an Asus q500a. It is using an Intel i5-3210M and Intel HD 4000 graphics.[/FONT][/COLOR]

---

### Post by grahammechanical on 2013-12-28
You could try selecting Recovery mode>Resume. It in the Advanced Option for Ubuntu sub-menu. It will load Ubuntu with a subset of the Nouveau open source video driver called llvmpipe. It can be used as a fallback for machines with graphic adapters that are not powerful enough to run accelerated graphics. You may have a video driver problem. If you can get to a desktop you can try changing video drivers. System Settings>Software and Updates>Additional Drivers tab. You need to be connected to the internet and you need to allow the utility time to find the drivers.

Oh, by the way, you will find the llvmpipe does not give a great user experience. But as a fallback in these circumstances it does the job.

Regards.

---

### Post by ogdencam on 2013-12-28
Trying what you suggested results in a command line interface. Is there a way I could fix the drivers through the terminal?

---

### Post by ogdencam on 2013-12-28
Bump.

---

### Post by oldfred on 2013-12-28
Is it just the Intel graphics or do you also have dual graphics.
With Intel there is only the i915 open source driver and it is the default. 
Usually with i915 nomodeset does not work but other boot options may.

Often this works but see link below for others
 acpi_osi=Linux  acpi_backlight=vendor


        Other video options - see post by Ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839](http://ubuntuforums.org/showthread.php?t=2184839)

---

### Post by ogdencam on 2013-12-28
> [COLOR=#000000][FONT=Ubuntubeta] Often this works but see link below for others[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]acpi_osi=Linux acpi_backlight=vendor[/FONT][/COLOR]
I tried that, but I still had the same problem. Trying to use boot-repair did nothing for me here is the link it provided me:
[http://paste.ubuntu.com/6654573/](http://paste.ubuntu.com/6654573/)

Disabling fast start/boot didn't help either.

---

### Post by oldfred on 2013-12-28
You are past what Boot-Repair can help with as you are booting into grub. 
Now it is video or perhaps other boot parameters also.
Did you try some of the other suggestions in the link? It seems to vary by specific model of Intel chip.

---

### Post by ogdencam on 2014-01-02
I followed all the suggestions in the link, but to no avail. Are there any other options?

---

### Post by jeanjd63 on 2014-01-02
Hello 
In a terminal, can you do this :
**lspci -nnv  | grep -i vga**

---

### Post by ogdencam on 2014-01-05
Using lspci -nnv | grep -i vga gave me this: 00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core pprocessor Graphics controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])

---

### Post by oldfred on 2014-01-06
Another Asus model needed this boot parameter.

[COLOR=#333333][FONT=UbuntuRegular]       [/FONT][/COLOR] pci=nomsi

One user actually put all the boot parameters into the Linux line. I would have expected some to conflict but for him it worked. I am sure only some were needed.

    [COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]

---

### Post by ogdencam on 2014-01-29
Sorry for the late reply, but [COLOR=#000000]pci=nomsi did nothing for me.[/COLOR]

---

### Post by oldfred on 2014-01-30
It seems like whatever you had originally worked. 
Any idea what updates were done that then caused it to break? Did you install anything new that might cause issues with graphics or screen. 

It may not be video driver but something in the loading of modules.

Try booting and in grub remove quiet splash to see where it stops. I usually stops at battery state command, but several lines above may be an error. Or it may just be the no screens found issue.

---

