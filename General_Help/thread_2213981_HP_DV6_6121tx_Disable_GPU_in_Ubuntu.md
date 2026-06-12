---
title: "HP DV6 6121tx: Disable GPU in Ubuntu"
date: 2014-03-29
forum: General Help
---

### Post by nilesh6 on 2014-03-29
I want to run ubuntu(13.04) on a live usb on my laptop. Now the problem  is that my 6770M is "broken"(it overheats a lot when switched on and  shuts down the computer). So when i run ubuntu i see the ubuntu logo and  then my laptop shuts down in few seconds. 
So is their any way that it does not power up the 6770M and just use the  HD3000? Like some special mode without graphic driver perhaps?
 
I tried googling a lot but only way to disabling gpu i found was to open  terminal which i cant because my laptop shuts down way before that.
EDIT: My laptop is HP DV6 6121tx and their is no option in bios for  this. But there is option to chose between switchable graphic mode and  fixed mode

---

### Post by su:bhatta on 2014-03-29
Did you try choosing from the BIOS 'Fixed Mode' GPU and not switchable graphics.

---

### Post by nilesh6 on 2014-03-29
yes i did but it doesn't affect it.It still uses the discrete graphic card

---

### Post by David D. on 2014-03-29
Do you mean 13.10?  13.04 reached End OF Life (EOL) in January.  EOL means it is no longer supported with updates and the repositories have been moved.  You would have trouble with adding anything to 13.04.

---

### Post by nilesh6 on 2014-03-29
i already had a copy of 13.04 so i thought i would try that first

---

### Post by su:bhatta on 2014-03-30
Suggest trying 13.10 it has a newer kernel. Not like that is going to fix the problem if it is Hardware problem.

If your Graphics is broken, then you have to first find a way to either replace the 6770M.
Does the HP website give you an option to download a newer version for BIOS of your MB, then you can download and see if that helps in turning off your troublesome 6770M.

---

### Post by SeijiSensei on 2014-03-30
"Fixed mode" forces the machine to use the ATI card.  If you switch that off in the BIOS, you should end up using the Intel adapter.  I had to enable fixed mode to use the ATI card in this dv6t.

---

### Post by nilesh6 on 2014-03-30
> **bhattabhishek said:**
> Suggest trying 13.10 it has a newer kernel. Not like that is going to fix the problem if it is Hardware problem.

If your Graphics is broken, then you have to first find a way to either replace the 6770M.
Does the HP website give you an option to download a newer version for BIOS of your MB, then you can download and see if that helps in turning off your troublesome 6770M.
it is not a problem with ubuntu so 13.10 is not goin to fix it unless a option for safe mode in which gpu drivers are not loaded was added (or is it already present in 13.04?)
is it possible to delete the gpu drivers or making ubuntu not load them? or make it ignore the gpu present?

I checked the hp website there was not any bois update
> **SeijiSensei said:**
> "Fixed mode" forces the machine to use the ATI card.  If you switch that off in the BIOS, you should end up using the Intel adapter.  I had to enable fixed mode to use the ATI card in this dv6t.
fixed mode just alows you to switch you gpu manually under os with proper software.
It was released because people were having performance issues with switchable graphic mode

---

### Post by su:bhatta on 2014-03-30
> **nilesh6 said:**
> it is not a problem with ubuntu so 13.10 is not goin to fix it unless a option for safe mode in which gpu drivers are not loaded was added (or is it already present in 13.04?)
is it possible to delete the gpu drivers or making ubuntu not load them? or make it ignore the gpu present?


Well, there is the Recovery Mode and see if starting in the TTY gives you a session : [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Also, see this : [http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4](http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4)

Also, read up the following links and see if something can come handy. 
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://ubuntuforums.org/showthread.php?t=2076352](http://ubuntuforums.org/showthread.php?t=2076352)

It all depends on if you can start Recovery Mode with TTY. Then you can test these.

---

### Post by nilesh6 on 2014-03-30
> **bhattabhishek said:**
> Well, there is the Recovery Mode and see if starting in the TTY gives you a session : [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Also, see this : [http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4](http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4)

Also, read up the following links and see if something can come handy. 
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[http://ubuntuforums.org/showthread.php?t=2076352](http://ubuntuforums.org/showthread.php?t=2076352)

It all depends on if you can start Recovery Mode with TTY. Then you can test these.
I tried pressing shift while using my live usb but it didn't work. Is there a Recovery mode in Live USB?

---

### Post by su:bhatta on 2014-03-30
Really, you have to read up a little, it was in the first link I provided : 
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

But I really doubt if that will help. You have to get rid of that faulty hardware, no other way.

---

