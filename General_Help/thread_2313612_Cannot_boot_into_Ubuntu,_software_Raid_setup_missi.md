---
title: "Cannot boot into Ubuntu, software Raid setup missing /dev/sdXX"
date: 2016-02-14
forum: General Help
---

### Post by seanelvidge2 on 2016-02-14
Hi all, really hoping someone will be able to help me out. 

When I boot up my machine I'm getting the BusyBox <initramfs> #command# thing. Looking around this forum it seems to suggest that this is because grub can't work out where to boot from. I found a good guide on how to resolve this ([http://ubuntuforums.org/showthread.php?t=1561735](http://ubuntuforums.org/showthread.php?t=1561735)). So I've been following the steps but I get stuck near the end and could really do with some help getting me back to a workable system. 

I've got a software raid set up, with an awful lot of stuff on it that I can't afford to loose so simply wiping everything and starting again is not an option for me. I'll walk through the steps I've done and highlight where I am stuck:

I've got into the grub prompt (by pressing c on the grub screen) and then typed:
```
ls
```
for a list of all the drives and partitions. The partition which contains the vmlinuz and initrd is (md/1) so I do:
```

set prefix=(md/1)/boot/grub
set root=(md/1)
set
ls /boot
insmod /boot/grub/i386-pc/linux.mod

```
Next the guide says I should do a 
```

linux /vmlinuz root=/dev/sdXY

```
Picking the 'correct' value of XY for my partition. This is where I get stuck. I don't have any such sdXY in /dev/. If I list the contents of /dev/ I get:
```

grub> ls /dev/

agpgart audio audio1 audio2 audio3 audioctl console core dsp dsp1 dsp2 dsp3 fd full kmem loop0 loop1 loop2 loop3 loop4 loop5 loop6 loop7 mem midi0 midi00 midi01 midi02 midi03 midi1 midi2 midi3 mixer mixer1 mixer2 mixer3 mpu401data mpu401stat null port ptmx pts/ ram ram0 ram1 ram10 ram11 ram12 ram13 ram14 ram15 ram16 ram2 ram3 ram4 ram5 ram6 ram7 ram8 ram9 random rmidi0 rmidi1 rmidi2 rmidi3 sequenceer shm smpte0 smpte1 smpte2 smpte3 sndstat stderr stdin stdout tty tyy0 tty1 tty2 tty3 tty4 tty5 tty6 tty7 tty8 tty9 urandom zero

```
I need to work out what to use for /dev/sdXY in the steps, then I think the next steps would be to run 'initrd /initrd.img' and 'boot'.

[B]EDIT
[/B]I've just tried looking in the mdadm.conf file:
```
cat /etc/mdadm/mdadm.conf
```
and it listed the device as /dev/md/1. So I tried running:
```

linux /vmlinuz root=/dev/md/1
initrd /initrd.img
boot

```
But it just booted into BusyBox with the error '/dev/md/1 doesn't exist'

---

