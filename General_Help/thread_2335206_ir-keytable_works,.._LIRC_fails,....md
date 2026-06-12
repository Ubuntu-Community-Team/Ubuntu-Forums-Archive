---
title: "ir-keytable works,.. LIRC fails,..."
date: 2016-08-26
forum: General Help
---

### Post by diyhouse on 2016-08-26
OK,.. I have trawled various forums and wiki's,.. but I am now beginning to struggle as to where next,...

I have a base mythtbuntu 16 system installed.... using TBS tuner cards,.. all installed with their respective drivers,.. and running OK

I can run:- sudo ir-keytable -c -p RC-5,LIRC -t -d /dev/input/event9   ( so my input device is good )

and then pressing remote control keys causes stuff to be written to the window....

If I then run;- sudo lircd --nodaemon --device /dev/input/event9 --driver devinput ( where lircd.conf points to a remote.conf created using irrecord... ) ,

Running irw and pressing remote keys produces no output. 

 So what is it that ir-keytable doing for me,.. that lirc is not managing... what am I missing,..  is ir-keytable an essential,.. or am I just missing the obvious with lirc

My conf file *includes *the following file:- 
> #

begin remote


  name  jvc.conf
  bits            8
  flags SPACE_ENC|NO_HEAD_REP|CONST_LENGTH
  eps            30
  aeps          100


  header       8403  4233
  one           475  1630
  zero          475   577
  ptrail        475
  pre_data_bits   8
  pre_data       0xC2
  gap          46293
  toggle_bit_mask 0x0


      begin codes
          KEY_PLAY                 0x30
          KEY_0                    0xCC
          KEY_1                    0x84
          KEY_2                    0x44
          KEY_3                    0xC4
          KEY_4                    0x24
          KEY_5                    0xA4
          KEY_6                    0x64
          KEY_7                    0xE4
          KEY_8                    0x14
          KEY_9                    0x94
          KEY_0                    0xCC
          KEY_DELETE               0x6C
      end codes


end remote




---

### Post by diyhouse on 2016-08-28
Have played some more,.. I can use irrecord to create a new remote file,...  store this in the lirc folder,.. and point to it from the lircd.conf file....

Then running the lircd of the command line,.. and running irw in another window,... IR button presses produce no output,.. even though I can

> cat /dev/input/event9

and get some garbage on screen,.. proving ( I think ) that the IR input is receiving something,... so why is it that lirc does not seem to want to play ball,.. as though the IR data is not being passed to lirc...

What am I still missing..

---

### Post by diyhouse on 2016-09-12
As a matter of closure on the thread,..  I did eventually get my system remote to fly....  however, I had to concede I had to run ir-keytable to load and setup some tables,... for use by lirc.....

Why no codes are passed without ir-keytable I do not know.

However from a debugging all the unknowns POV when setting up lirc,... running

> [COLOR=#000000]sudo lircd --nodaemon --device /dev/input/event9 --driver devinput[/COLOR]

Of the command line was key,...  as I later discovered when trying to run lirc as a service... as along the way I had set one of the control flags incorrectly....

---

