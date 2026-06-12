---
title: "OMG readahed! need help!"
date: 2006-10-31
forum: General Help
---

### Post by louistan3 on 2006-10-31
omg.. i posted earlier about boot times about 25s.. but now.. sumthn happend and my boot is up to 36s now.. i thnk its the readahead-list thats slowin me down.. can anyone help me fix this? 

here are my 2 bootcharts 

pls help me! :-S

---

### Post by louistan3 on 2006-10-31
dont mind the fsck.. its a forced one.. but im pretty sure its the readahead list.. pls help!

---

### Post by kerry_s on 2006-10-31
The perils of speed. Don't use preload or prelink that slows it down. the readahead should pick up after a couple of reboots the first will be slow. You did just run it once and remove it right?

---

### Post by louistan3 on 2006-10-31
i dont think i use preload or prelink.. :-S

it just sucks coz i gained 10s on my boot time.. pls help anyone?

---

### Post by kerry_s on 2006-10-31
You can uninstall readahead, i don't have it installed on mine, but i'm using a edgy server install build up.

---

### Post by louistan3 on 2006-10-31
yey! the previous post was right.. i had preload in boot up manager.. i just turned it off.. deleted the readahead file.. and did a reprofile and its back.. thanks for the help! :D

---

