---
title: "Not able to view the desktop"
date: 2013-07-07
forum: General Help
---

### Post by haydenljohnson on 2013-07-07
Hello all,
I must admit that I am very new to linux and ubuntu. I downloaded ubuntu 12.04 LTS onto my gateway pc. I wanted to do this because I found out my pc had a counterfeit version of windows 7 on it. I had successfully downloaded ubuntu onto it, and was enjoying it. Everything worked good, until I decided to download Cinnamon interface onto it. I decided I didn't like it, so I looked up a website with some terminal code to insert that claimed it would erase it. It ended up erasing a lot more. I turned off the computer and powered it on. I see the start up gateway logo and I then see the purple screen with the ubuntu logo and the loading dots, then instead of going into the login screen and the visual desktop, it goes straight to a black screen (similar to terminal). The screen asks me to insert my username and password, which I do, but then it continues to go to the black screen instead of the visual ubuntu desktop. Please help me. I really need this to be fixed. 

Thanks
-GB ~Hayden

---

### Post by Bucky Ball on 2013-07-07
Welcome to the forums. Do you end up at a black screen, no cursor, you can't type anything? Just a black screen? If you have a cursor, try typing 'startx' or 'lightdm'.

Provide a link to the page you followed to uninstall Cinnamon. I haven't used it but believe it is a desktop environment. You can choose which desktop environment to use at the login screen. For next time, if you installed Cinnamon through a PPA you could have uninstalled the PPA or gone to Synaptic Package Manager or Software Centre, search for 'Cinnamon' and uninstall. It's that simple in Ubuntu, not like Windows.

Always look to install stuff through the official repositories and remove the same way. If you add a third-party repository (which may be the case for Cinnamon, could you provide a link for how you installed) you can unistall the app via Synaptics/Software Centre and just leave the PPA or remove that too. 

When you boot the machine, start hitting the shift key (could be escape on 12.04). Does that get you to the menu list with a selection of kernels and Windows if you're dual-booting? If so, choose the recovery kernel (second on the list) and when you get to the options, choose to boot to a root shell and install the desktop environment you were using (for a straight Ubuntu 12.04 LTS install that would be Unity). Issue this:
```

sudo apt-get install unity
```

That should make sure it is all there. Type exit then continue normal boot from the options. How did all that go?

* Update: Looking here:

[http://cinnamon.linuxmint.com/?page_id=61](http://cinnamon.linuxmint.com/?page_id=61)

... it appears to be a PPA. In future, simply use Synaptics/Software Centre to uninstall. After that you can clean up a bit more by issueing this in a terminal:

```
sudo apt-get autoremove
```

Will get rid of any leftovers/orphans/flotsam.

---

### Post by haydenljohnson on 2013-07-08
Hello,When I turn on the computer this is usually what I get:*Starting the Winbine daemon winbind                                                                                                                                                                         [ ok ]saned disabled; edit /ect/default/saned*Stopping cold plug devices                                                [ ok ]                                                                                                         [ ok ]*Stopping log initial device creation                                                                                                         [ ok ]*Starting configure virtual network devices                                                                                                         [ ok ]*Stopping configure virtual network devices                                                                                                         [ ok ]*Starting configure network device security                                                                                                          [ ok ]*Stopping anac(h)ronistic crom                                                                    [ ok ]^@_ It has no mouse, nothing but a flashing line that can be used for typing. I have tried what you said, but I am not running dual. I only have ubuntu on my computer. Would there be anyway of clearing this all up? I really hope to get this problem resolved. -GB ~hayden

---

### Post by BreezyBrooke on 2013-07-08
Run these commands, they should fix everything. make sure to put them all in at once like typed below.

sudo apt-get install ubuntu-desktop && sudo apt-get install --reinstall ubuntu-desktop && sudo apt-get install --fix-policy && sudo apt-get --purge autoremove && sudo apt-get autoclean

---

### Post by haydenljohnson on 2013-07-10
I submitted the code just like you had instructed, but I got and error message, I had it written down, but I cannot find it at the moment. I did what the instructions in the error message stated, but then I just got more errors upon errors.

---

