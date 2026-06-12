---
title: "Login Loop Situation"
date: 2018-03-22
forum: General Help
---

### Post by dantruong02 on 2018-03-22
Hi there! I just started giving open source OS a try, but I got stuck at the very beggining. I installed Ubuntu 16.04 on dual boot with Windows 10. Then I installed the NVIDIA driver for my GTX 970, some packages and that was it. The thing is, when I reboot, after I try to login on Ubuntu I get a black screen with the message:
[HTML]/dev/sda6: clean 5407/1221600 files, 215410/2441872 blocks[/HTML]

Then it goes back to the login screen. I looked it up and figured I'd have to boot from a live CD, then stop the fsck system. But whenever I try to boot from the CD, after I select "Boot from first hard disk", I get this message:
[HTML]Booting from local disk…Boot failed: press a key to retry…[/HTML]

And now I'm stuck. I tried some other things, and already reinstalled Ubuntu three times, always with the same problem. Oh, and for what is worth, I got this:

```

/dev/sda1 (inicializar); Start: 2048; Fim: 206847; Setores: 204800; Size: 100M; Id: 7; Tipo: HPFS/NTFS/exFAT
/dev/sda2; Start: 206848; Fim: 1365608227; Setores: 13654013800; Size: 651,1G; Id: 7; Tipo: HPFS/NTFS/exFAT 
/dev/sda3; Start: 1951680512; Fim: 1952602111; Setores: 921600; Size: 450M; Id: 27; Tipo: WinRE de NTFS oculto
/dev/sda4; Start: 1365608446; Fim: 1951680511; Setores: 586072066; Size: 279,5G; Id: 5; Tipo: Estendida
/dev/sda5; Start: 1935034368; Fim: 1951680511; Setores: 16646144; Size: 8G; Id: 82; Tipo: Linux swap
/dev/sda6; Start: 1365608448; Fim: 1935034367; Setores: 569425920; Size: 271,5G; Id: 83; Tipo: Linux

```

---

