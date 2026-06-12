---
title: "Vnstat reporting large amount of traffic"
date: 2024-06-26
forum: General Help
---

### Post by lumaja on 2024-06-26
[SIZE=3]Ubuntu 24.04[/SIZE]
  [SIZE=3]Vnstat ver: 2.12[/SIZE]
  
 
  [SIZE=3]Vnstat some days reports very high traffic different than provider.[/SIZE]
  [SIZE=3]On 24 Jun again reports[/SIZE]
  
 
  [SIZE=3]hour		rx		tx		total[/SIZE]
 07:00        3.10 GIB	     3.95 GIB	       7.05 GIB
 Total for the day [FONT=Liberation Serif, serif][SIZE=2] 8.43 GiB[/SIZE][/FONT]
 
 
 [FONT=Liberation Serif, serif][SIZE=2]The provider reports total [/SIZE][/FONT][FONT=Liberation Sans, serif][SIZE=2]1862 [/SIZE][/FONT][FONT=Liberation Sans, serif][SIZE=2]MB[/SIZE][/FONT]
 
 
  [FONT=Liberation Sans, serif][SIZE=2]Can some help to correct this[/SIZE][/FONT]
  [FONT=Liberation Sans, serif][SIZE=2]Thank you[/SIZE][/FONT]

---

### Post by currentshaft on 2024-06-26
What is "the provider"? Your ISP?

They would only account for Internet traffic, whereas vnstat might be counting local network traffic also.

---

### Post by lumaja on 2024-06-27
The provider" is Your ISP.
 Vnstat is installed on desktop and monitors only the desktop traffic ([FONT=Liberation Sans, serif][SIZE=2]wlx14ebb61933fb).[/SIZE][/FONT]
  [FONT=Liberation Sans, serif][SIZE=2]The wifi router only connection is the desktop. It is impossible for vnstat record more traffic[/SIZE][/FONT]
  [FONT=Liberation Sans, serif][SIZE=2]than ISP.[/SIZE][/FONT]
 [FONT=Liberation Sans, serif][SIZE=2]The time that [/SIZE][/FONT][FONT=Liberation Sans, serif][SIZE=2]report high traffic twice was 7:00 AM from about 6:30 AM to about 7:20 AM[/SIZE][/FONT]
 [FONT=Liberation Sans, serif][SIZE=2]I always having breakfast and watch the TV News I am away from the computer.  [/SIZE][/FONT] 
 [FONT=Liberation Sans, serif][SIZE=2]I had [/SIZE][/FONT][FONT=Liberation Sans, serif][SIZE=2]vnstat report t[/SIZE][/FONT][FONT=Liberation Sans, serif][SIZE=2]hese error before at [/SIZE][/FONT][FONT=Liberation Sans, serif][SIZE=2]11:00 AM when I was in a meeting,[/SIZE][/FONT][FONT=Liberation Sans, serif][SIZE=2] [/SIZE][/FONT]

---

### Post by currentshaft on 2024-06-27
Install Wireshark. When you don't expect to see traffic:

tcpdump -i any -w save.pcap

Go enjoy your breakfast and morning news.

Come back and run:

tshark -r save.pcap -q -z conv,ip

That'll show you where the packets went.

---

