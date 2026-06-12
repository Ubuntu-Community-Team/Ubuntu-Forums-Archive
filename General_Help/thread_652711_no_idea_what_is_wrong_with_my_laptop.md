---
title: "no idea what is wrong with my laptop"
date: 2007-12-29
forum: General Help
---

### Post by n0greenfx on 2007-12-29
hey, my grlfriend just gave me here laptop because it seems to have something wrong with it i cant figuer out what. basically what happens is every time i boot into windows it freezes up after a few minutes and i cant do anything at all. i am able to run the pc in windows safe mode with no problem at all..i am think its a problem with the windows install that is on the but currently i have no windows cd's to reinstall it...so at the moment i am installing ubuntu i seem to be able to run off the live cd with no problem as long as i keep the laptop sitting stable on my desk....it may also be that the harddrive is just broken and it cant be fixed i have no idea..ii hope installing ubuntu and reformatting the hdd will fiix this problem...if anyone has any ideas what this may be please help

---

### Post by scxtt on 2007-12-29
overheating?

---

### Post by n0greenfx on 2007-12-29
i dont think so the fan seems to be working the bottom doesnt seem to get to hot idk how else to check for overheating

---

### Post by n0greenfx on 2007-12-29
ok i got ubuntu installed fine and i just moved it from the desk to my lap and it froze up on me :(

---

### Post by n0greenfx on 2007-12-29
could there be something loose inside of it?/

---

### Post by Ripfox on 2007-12-29
Yes. :)

---

### Post by n0greenfx on 2007-12-29
i found the hdd iv never really messed with laptops before...the hdd was on the side of the pc in a slot that u can just pull out and the screw was missing so it was rathe3r easy to pull out i fixed that and i still have the problem. may the hdd have bad sectors on it does that sound like the problem, but ubuntu install perfectly fine so to me it seems the hdd is fine. at the moment i dont have a small enough screwdriver to open up the laptop so i may hafta wait till tomorow.

---

### Post by n0greenfx on 2007-12-29
i just dont understand when i had the pc in windows safe mode i could carry it around and all with no freezes

---

### Post by Ripfox on 2007-12-29
Did you wipe the Windows partition completely and start over with a fresh Ubuntu?

---

### Post by n0greenfx on 2007-12-29
yes i did

---

### Post by Ripfox on 2007-12-30
Hmm...have you checked to see if the hdd is seated correctly as well as the ram?

---

### Post by n0greenfx on 2007-12-30
hdd is in correctly its a strange slot loading hdd u can pull out of the side i can not getting into the ram i still have not gotten the correct screw drivers

---

### Post by Ripfox on 2008-01-02
Could be improperly seated ram or simply bad ram?

---

### Post by Whiffle on 2008-01-02
Sounds like a stick of loose ram to me.

---

### Post by n0greenfx on 2008-01-02
i took out the ram and made sure its in properly i have no idea how to check if the ram is bad.....for some reason im thinkin it may be and hdd with bad sectors??

---

### Post by Lacrimstein on 2008-01-02
To test the RAM for errors, you can use memtest utility, which is available from the GRUB boot menu.

---

### Post by n0greenfx on 2008-01-02
i ran memtest and it passed all the tests the test tok forever like over 4hrs

---

### Post by Lacrimstein on 2008-01-02
You know, it's really weird that the hdd is slotload. Usually primary hdd's aren't like that. I think you should check if there is another hdd in nautilus. Also try:

fsck -C /

This will check the drive for errors. Not sure on the exact syntax or some options you may need for repair, so check the man pages.

---

### Post by n0greenfx on 2008-01-02
i checked the whole pc opened it up and all and there is no other hdd in there ill try running that chk disk thing in the terminal tho....by the way iv actually never seen a slot loaded hdd

---

### Post by n0greenfx on 2008-01-02
damn thing wont go passed the loading screen without freezing i guess ill try running memetest again

---

### Post by Lacrimstein on 2008-01-02
try to boot into recovery mode and do it from there.

---

### Post by n0greenfx on 2008-01-02
Ok I let it sit and run memtest its been running for13hrs can I stop it yet it passed 39 tests. No error

---

### Post by n0greenfx on 2008-01-02
ok, i ran memtest no errors stopped the damn program after it pass like 59tests. the i booted into recovery mode and typed in fsck -c in the terminal. and ran that it checked all the blocks(read only) and the i got this error message.

[COLOR="red"]inodes thet were part of a corrupted orphan link list. fix (Y)[/COLOR]

i touched nothing and got this message

[COLOR="red"][266.778000} BUG: unable to handle krenel paging request at virtual adress ndle kernel paging request at virtual adress fffffff2 {2660.772000] printing eip:[/COLOR]

Then i was unable to anything but hold down the power button and reboot. at the reboot i got

[COLOR="red"]Grub Loading, please wait.........
error 2[/COLOR]

---

