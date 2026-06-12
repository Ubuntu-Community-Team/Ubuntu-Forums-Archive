---
title: "Sbackup broke in Feisty"
date: 2007-04-25
forum: General Help
---

### Post by johanPO on 2007-04-25
With the upgrade from 6.10 to Feisty sbackup stopped working. Running it in a terminal gives 

johan@johans:~$ sudo sbackupd 
I: Securing permissions at: /media/IOMEGA_HDD/usb_backup/2007-04-22_21.00.01.922346.johans.ful
I: Upgradeing to v1.3: /media/IOMEGA_HDD/usb_backup/2007-04-22_21.00.01.922346.johans.ful
Traceback (most recent call last):
  File "/usr/sbin/sbackupd", line 404, in <module>
    upgrader.upgrade_target( target, purge )
  File "/usr/sbin/upgrade_backups.py", line 60, in upgrade_target
    self.upgrade_tdir( target+"/"+adir )
  File "/usr/sbin/upgrade_backups.py", line 81, in upgrade_tdir
    self.upgrade_v13( tdir )
  File "/usr/sbin/upgrade_backups.py", line 107, in upgrade_v13
    flist = gnomevfs.read_entire_file( tdir+"/flist" ).split( "\n" )
gnomevfs.NotFoundError: File not found


This seems to be an error somewhere in the way python commands are working.. so lets test if it works on a file in my home directory.. it does

>>> gnomevfs.read_entire_file("/home/johan/test.sch").split( "\n") for instance
['<Qucs Schematic 0.0.9>', '<Properties>', '  <View=0,0,800,800,1,0,0>', '  <Grid=10,10,1>', '  <DataSet=test.dat>', '  <DataDisplay=test.dpl>', '  <OpenDisplay=1>', '</Properties>', '<Symbol>', '  <.PortSym 40 20 1 0>', '</Symbol>', '<Components>', '  <Port P1 1 160 230 -23 12 0 0 "1" 1 "analog" 0>', '  <R R1 1 190 230 -26 15 0 0 "50 Ohm" 1 "26.85" 0 "0.0" 0 "0.0" 0 "26.85" 0 "european" 0>', '  <C C1 1 260 230 -26 17 0 0 "1 pF" 1>', '  <R R2 1 290 260 15 -26 0 1 "50 Ohm" 1 "26.85" 0 "0.0" 0 "0.0" 0 "26.85" 0 "european" 0>', '  <GND * 1 290 300 0 0 0 0>', '</Components>', '<Wires>', '</Wires>', '<Diagrams>', '</Diagrams>', '<Paintings>', '</Paintings>', '']

It seems like that duing the upgrade the usb drive has gotten a second entry. I now have IOMEGA_HDD and IOMEGA_HDD_

johan@johans:~$ ls -l /media/IOMEGA_HDD*
/media/IOMEGA_HDD:
total 4
drwx------ 3 root root 4096 2007-04-25 21:24 usb_backup

/media/IOMEGA_HDD_:
total 32
drwx------ 42 johan root 32768 2007-04-22 11:55 usb_backup

Interesting is also that the owner of the drive has changed. 

By changing to the "new" drive IOMEGA_HDD_ the backup works

---

### Post by johanPO on 2007-04-30
Here is what I am getting from /var/log/syslog. 

Apr 30 21:00:01 johans /USR/SBIN/CRON[31948]: (root) CMD (if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;)

---

