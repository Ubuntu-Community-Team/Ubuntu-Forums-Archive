---
title: "Logkeys output file"
date: 2013-05-29
forum: General Help
---

### Post by tsi25 on 2013-05-29
I have ubuntu 12.10 64 bit 

I got several roommates that like to dink around on my computer sometimes, rather than just locking them out i kinda want to know what theyre up to so i installed logkeys (a keylogger). i got it installed through the ubuntu software center, so i think its an older version; logkeys 0.1.1a-3. i got it to start and halt through the command prompt with sudo logkeys --start and sudo logkeys --kill, and i made a new file for the output to be put into with "touch Desktop/test/test.log" and then again later with "touch Desktop/test/log.txt"

then i tried to start by running "sudo logkeys --start --output Desktop/test/test.log" but when i typed out the keyboard and opened the file it was blank. i tried halting the program to see if maybe it doesnt update in real time and needs to halt before it updates; that left the file blank too. i thought maybe the problem was that it was a .log and not a .txt so i tried this whole process again with a .txt but still its a blank file.

it seems to be running ok but theres no output. how do i access output? or put the output in a location that can be easily accessed?

---

### Post by bhencetotozo on 2013-10-19
You are not the only one with the same problem...

logkeys works perfect in 2 different machines that I have. With an older ubuntu version, and also Backtrack.

But with 12.04 64 bits, the output file is empty.

It creates the file, but the file is 100% empty... I pointed the map file, I tried with out pointing it... It just doesn't work.

I tried to install the latest version manually, and I also tried to get it from the software central from ubuntu's launcher. 

It installs fine both ways, but none of them works...

I also tried LKL, doesnt work. 

I tried pykeylogger, does not work neither.

I don't know what the issue is.

---

