---
title: "Won't boot &quot;The disk drive for /dev/mapper/ubuntu--vg-swap_1&quot; help?"
date: 2014-03-02
forum: General Help
---

### Post by callumcole on 2014-03-02
Hi there,

I am very much a noob to Ubuntu so I was messing around getting used to it and decided to install backtrack. I found a youtube tutorial and followed the commands on terminal, anyway after re-booting I got this message "The disk drive for /dev/mapper/ubuntu--vg-swap_1" with 'press s to skip or m for manual configuration' but they both lead me to a black screen and it stays like that. here is the code I pasted in; 

> sudo passwd root
sudo sh -c 'echo "greeter-show-manual-login=true" >> /etc/lightdm/lightdm.conf'
sudo apt-get install gnome-session-fallback
sudo apt-get install gdebi && sudo apt-get install synaptic

Any help would be very greatfull, and if I could ask for you to explain to me as if I was mentally handicapped that would help. 

Thank you in advance,
Callum

---

