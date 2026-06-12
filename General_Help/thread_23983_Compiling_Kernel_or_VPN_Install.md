---
title: "Compiling Kernel or VPN Install"
date: 2005-04-04
forum: General Help
---

### Post by core on 2005-04-04
I wanted to establish a VPN connection to my faculty as I do under windows with ease. They have there some tutorial to do so under red hat 8 and it's not updated at all. SO as I was unsucessful, i decided to ask for help in newsgroups, where a friend of mine said he had this tutorial with his own way of getting vpn connection established under debian. but soon the problems begin.
It says for me to do
> sudo apt-get install pptp-linux ppp kernel-patch-mppe kernel-package debhelper dpkg-dev kernel-source-2.6.Y 
where Y is an appopriate version. The thing is, kernel-source 2.6.9 is the most recent I could find in repositories. And my version seems to be 2.6.10, so I didn't want to mess with kernel compiling as it says further in his tutorial.

My questions are: is it ok to compile an older version of the kernel? And, is this really needed to get vpn connection running on my ubuntu box?

With some instructions in portuguese, here goes the first part of his tutorial, in case it helps
> O Y e um numero escolhes a versao que te der mais jeito
sudo apt-get install pptp-linux ppp kernel-patch-mppe kernel-package debhelper dpkg-dev kernel-source-2.6.Y
cd /usr/src
sudo tar xvfj kernel-source-2.6.Y.bz2
cd kernel-source-2.6.Y
cp /boot/config-2.6.Y .config
sudo make-kpkg --added-patches mppe --config menuconfig kernel_image


depois seleccionas:
device drivers -->

e de seguida
networking support -->


activas o suporte para PPP como modulo
<M> PPP (point-to-point protocol) support


e colocas o resto da mesma forma que abaixo
[ ] PPP multilink support (EXPERIMENTAL)
[*] PPP filtering
<M> PPP support for async serial ports
< > PPP support for sync tty ports
<M> PPP Deflate compression
<M> PPP BSD-Compress compression
<M> PPP MPPE compression (encryption)


exit exit exit (e indica que queres gravar a nova configuração do kernel)
vai tomar um café (deixas a compilar)


cd ..
depois instalas o kernel que acabaste de compilar
sudo dpkg -i kernel-image-2.6.Y_10.00.Custom_i386.deb (o nome pode ser ligeiramente diferente) 

Thanks in advance.

---

