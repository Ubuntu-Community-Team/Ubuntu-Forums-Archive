---
title: "Breezy with Win2k dual boot"
date: 2005-10-26
forum: General Help
---

### Post by Kjell on 2005-10-26
Sorry this my not be a Ubuntu issue, but of the win2K

I thought I re orginaize my hard drive partitions when Brezzy arrived, as: 
1. for Win2k (10 gb for system testing)
2. for /root   (30 gb)
3. for /home   (100 gb)
& swap 

First I install win2k, I had to remove all partitions in order for win2k to format a partition & accept to install, after this win2k boots OK.

After this I install Ubuntu,  when I reach the partition section I create separate  partitions (ex3) for /root and for /home, and also swap.

Then adding Grub to MBR 

After finnsihing all the Ubuntu installation, re booting ...  
I get the Grub menue - to start Ubuntu is OK 
but when I choose win2k - win2k boots. first I see the first b/w screen, after this 
I see the second colored boot screen untill the "rolling bar" comes half way- 
then I get the Blue screen. 

The blue screen erorr message is that there is some virus or defekt on the HD and I should run chkdsk /f to repair it ?   

I've tried at least 6 diferent installations in this manner but with different partitions
- I alwas get the blue screen with win2K

Previously I used Ubuntu 5.04 with dual boot No problem. 

I installed Ubuntu 5.10 on my Dell laptop without any problem, with same partitons as above. 

I belive that the MBR is OK as GRUB starts OK and also that win2K starts to boot, eventhough it I get the bleu screen when it during the booting process.

Any ideas ?

---

### Post by John.Michael.Kane on 2005-10-26
Frist install your windows os. then when you install 5.10 let it resize the free space  it will give you the option to do this. after that you should be able to have dual boot.

---

### Post by Kjell on 2005-11-01
Thanks for you replay Plissken,

Well, I tried to let the breezy 5.10 do the recomend hard disk partioning
No luck, Win2K still craches. When I try to start it start in safe mode 
and then trying to repair it, it says that there is no win2k existing on my hard drive ! 

I Cant belive that 5.10 makes any writing to the win2k partition, but it appears like that. 

I Just dont understand why it worked earlier  

Well, now Win2k is removed and I'm a purely running breezy - It feels good, couse now I'm FREE ....

//Kjell

---

