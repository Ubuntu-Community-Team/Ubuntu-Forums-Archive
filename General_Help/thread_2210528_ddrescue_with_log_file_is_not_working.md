---
title: "ddrescue with log file is not working"
date: 2014-03-11
forum: General Help
---

### Post by russo2 on 2014-03-11
im trying to use ddrescue with the log option, but its not working.


  so i have 2 HDs:
  /dev/sda - working 
/dev/sdb - bad

  
im booting from a live usb disk(Ubuntu 12.04.4 LTS)

  
so i mount the good hd(ntfs partition):

  sudo mount /dev/sda4 /media/backup 

  
/media/backup is working, i can write, save, etc... i didnt mount /dev/sdb, since its bad, also if i mount /dev/sdb, i can access it. 

  
then i try ddrescue: 

  ```
ddrescue -f -g -n /dev/sdb3 /media/backup/rescue.img  /media/backup/rescue.txt

  result: 
ddrescue: warning: Options -C -d -D -e -E -M -n -p -r -R -S -t  and -T ddrescue:          are ignored in generate-logfile mode.  ddrescue: Can't open output file: No such file or directory

  
ddrescue -f -g -n /dev/sdb3 /media/backup/rescue.img rescue.txt

  result:  ddrescue: warning: Options -C -d -D -e -E -M -n -p -r -R -S -t and -T ddrescue:          are ignored in generate-logfile mode. ddrescue: Can't open output file: No such file or directory

  
```

so it only work if i remove -g and the log file.

  what im doing wrong? why its not working?

---

### Post by russo2 on 2014-03-12
i was following a tutorial that had the -g option, i guess running it from the 1st time there is no need for -g 

just with this command:
ddrescue -f -n /dev/sdb3 /media/backup/rescue.img  /media/backup/rescue.log

i was able to save the entire partition, minus one directory.

I must add, that if u want to save your data, dont write on it and dont try to copy, via windows or whatever, 
if some how u cant see the hd or if u get an error during boot, just unplug the hd and let it cool, then load any live linux and 
go for ddrescue, dont mount the bad hd.

---

