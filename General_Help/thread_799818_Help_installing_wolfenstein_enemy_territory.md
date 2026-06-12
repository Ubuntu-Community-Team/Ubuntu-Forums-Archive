---
title: "Help installing wolfenstein enemy territory"
date: 2008-05-19
forum: General Help
---

### Post by snobby500 on 2008-05-19
Hi, i have looked for help to install enemy territory but i havent seen my problem yet..
I downloaded enemy territory (wolfenstein) and made it exacutable, but it doesnt run, so i looked and found some different ways of running it: here is the output of ther terminal when i run:
sudo sh et-linux-2.60.x86.run
i then got this output from terminal:

Verifying archive integrity...Error in MD5 checksums: d519aac10e03c72197193966fae9a9e8 is different from b8b59bc515d86cc845fb52f5d2c14423

i dont know how to get any further, could it be a bad download??

thanks in advance

p.s. i know its off subject but is there some way to check that your ubuntu download is ok after youve downloaded it?

---

### Post by snobby500 on 2008-05-19
dont worry, i downloaded it another time and it worked fine :)

---

### Post by canoemoose on 2008-05-19
> **snobby500 said:**
> could it be a bad download??

Probably, yes.  The checksum nonsense is checking to make sure the contents of the file are what they should be.  The error is returned because they aren't

> **snobby500 said:**
> is there some way to check that your ubuntu download is ok after youve downloaded it?

Indeed there is. If you've got a working Ubuntu install, do this:

[QUOTE=ssam]run md5sum on the file. if it matches with the md5sums at [http://releases.ubuntu.com/hardy/MD5SUMS](http://releases.ubuntu.com/hardy/MD5SUMS) then there is 99.999999999999999% chance that there is nothing wrong with the file. you could try reburning at a lower speed, or using higher quality CD-Rs.

```
7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe
```

i dont know of a good way to MD5SUM a file without using a terminal, but is its faily easy.

open a terminal (Applications->Accessories->Terminal)
type 'md5sum' (without the quotes) followed by a space
drag the icon of the file from the file browser to the terminal
press enter
wait a minute for the result[/QUOTE]

The result given by the terminal should match the MD5SUM given in the list above for the *.iso that you are checking.

Ah, never mind.

---

