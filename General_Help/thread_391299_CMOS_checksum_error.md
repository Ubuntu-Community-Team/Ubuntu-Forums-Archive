---
title: "CMOS checksum error"
date: 2007-03-23
forum: General Help
---

### Post by warlock_handler on 2007-03-23
Hi guys,
I have a small problem with my BIOS... this all started recently after I removed my floppy drive from my computer. I made the required changes in my BIOS, ie floppy =none and chk for floppy at boot = disabled; But now the problem starts... when I save and exit it works fine but the next time when I start my PC it gives my a CMOS checksum error and also says floppy drive not found. So basically it is not saving the changes I make in my BIOS. Need help guys!!

The very basic solution to this would be that the cell on my motherboard is dieing; So I changed the cell and still I keep getting this error at boot time. Can anyone please tell me where I am wrong?

my pc config:
2400+ atlon
Phoenix Award BIOS
512 RAM
blah blah blah

thnx

---

### Post by dfreer on 2007-03-23
By "cell" do you mean the CMOS battery? This does sound like a dead battery issue, but if that's the case your system clock should be messed up as well. My idea would be to try reseting all CMOS configuration data (either in BIOS or by removing the battery/changing the jumper). It should auto detect that there is no floppy drive.

Come to think of it, most of my older PII/PIII boards never complained when I removed the floppy drives. I would just leave the floppy drive enabled in BIOS...

---

### Post by warlock_handler on 2007-03-23
> **dfreer said:**
> By "cell" do you mean the CMOS battery? This does sound like a dead battery issue, but if that's the case your system clock should be messed up as well. My idea would be to try reseting all CMOS configuration data (either in BIOS or by removing the battery/changing the jumper). It should auto detect that there is no floppy drive.

Come to think of it, most of my older PII/PIII boards never complained when I removed the floppy drives. I would just leave the floppy drive enabled in BIOS...

interesting.. i think i will put back the floppy drive and see if that fixes it... if not.. then i will change the battery again...

---

### Post by dfreer on 2007-03-23
Let us know :)

---

### Post by warlock_handler on 2007-03-27
> **dfreer said:**
> Let us know :)

I reconnected my floppy drive and now i am still getting this 

"CMOS Error - reset to default"

before the boot.... SOSSSS .. HELPPPP

---

### Post by dfreer on 2007-03-27
What BIOS is installed (Version # would help too), and what Motherboard are you using?

---

### Post by warlock_handler on 2007-03-27
> **dfreer said:**
> What BIOS is installed (Version # would help too), and what Motherboard are you using?

Bios is Phoenix Award BIOS
Motherboard is ASUS

i dont quite know the version...

---

### Post by dfreer on 2007-03-28
This has some information on the Phoenix CMOS:
[http://www.phoenix.com/en/Customer+Services/BIOS/BIOS+FAQ/default.htm#Q9](http://www.phoenix.com/en/Customer+Services/BIOS/BIOS+FAQ/default.htm#Q9)

All CMOS does is store configuration data. (1) did you install a brand new fresh CMOS battery? (2) did you run BIOS setup after changing the battery and configure everything? (3) Take some detailed notes, try to listen for POST codes and write down ANY error messages on boot. (4) Try switching the CMOS Jumper to reset CMOS

This shouldn't be a huge issue, it should let you boot even without the CMOS battery installed (although it will complain on every boot and your system clock will always be wrong).

---

### Post by warlock_handler on 2007-03-28
> **dfreer said:**
> This has some information on the Phoenix CMOS:
[http://www.phoenix.com/en/Customer+Services/BIOS/BIOS+FAQ/default.htm#Q9](http://www.phoenix.com/en/Customer+Services/BIOS/BIOS+FAQ/default.htm#Q9)

All CMOS does is store configuration data. (1) did you install a brand new fresh CMOS battery? (2) did you run BIOS setup after changing the battery and configure everything? (3) Take some detailed notes, try to listen for POST codes and write down ANY error messages on boot. (4) Try switching the CMOS Jumper to reset CMOS

This shouldn't be a huge issue, it should let you boot even without the CMOS battery installed (although it will complain on every boot and your system clock will always be wrong).

Let me try your solution today, as of now

1) I put a new abttery
2) I had re configured the BIOS post that
4) I didnt try switching the jumper to reset CMOS.... will try that tonight

This thing is really bugging me... aaaaaaahhhhhhhhhh

---

### Post by warlock_handler on 2007-03-28
ohh btw.. there are no error beeps... while booting

---

### Post by dfreer on 2007-03-29
I dunno what to do from here. Could be a bad MoBo... hopefully someone else here can help you. Without any POST errors it's hard to diagnose. Sorry I couldn't help you with your problem, good luck!

---

### Post by warlock_handler on 2007-03-30
> **dfreer said:**
> I dunno what to do from here. Could be a bad MoBo... hopefully someone else here can help you. Without any POST errors it's hard to diagnose. Sorry I couldn't help you with your problem, good luck!

cool no problemo... i will figure it out... else i might just buy a new MB processor and graphics card for my this bday

---

