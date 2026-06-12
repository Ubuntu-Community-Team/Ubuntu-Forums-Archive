---
title: "Brasero - Speed and Finalisation"
date: 2018-03-19
forum: General Help
---

### Post by anon_private on 2018-03-19
Hello,

I used Brasero to burn an iso file to a DVD -R.

I set the write speed to 4x, and ticked the box so that files could be added after the burn.

To my surprise, the burn speed was usually well above 4x, and the disk was finalised.

Can anyone explain these phenomena, and suggest how I can initiate Brasero so that it obeys its instructions?

Thanks

---

### Post by raleigh3 on 2018-03-19
R means that it can only be written to once.

You need a RW disc.

---

### Post by scdbackup on 2018-03-20
Hi,

the write speed is effecyively chosen by the drive. The burn program can
only tell what it would like to have.
One can ask the drive about the supported speeds. E.g. with a "16x" DVD-R
i get offered by an ASUS BW-16D1HT drive: 8x, 12x, 16x. No 4x.

The real speed on DVD-R depends on the write position. It increases on
the way to the rim of the medium. Full nominal speed is often reached
only at the very end of the burn run.


The fact that the medium did not stay appendable is surprising.
Maybe Brasero obeys that check-box only with data compositions but not
with burning of readily formatted filesystem images.

The lengthy log of such a Brasero run might give hints what Brasero planned
to do.


raleigh3 wrote:
>  R means that it can only be written to once.

But it is supposed to be writable on its yet unused area after a
burn program kept it appendable.

Theoretically a DVD-R can take 99 sessions. In practice this is hardly
achievable because a dozen unused MB remain between each session.
But 30 sessions of incremental backups are well realistic.

Have a nice day :)

Thomas

---

### Post by anon_private on 2018-03-20
> **scdbackup said:**
> Hi,

the write speed is effecyively chosen by the drive. The burn program can
only tell what it would like to have.
One can ask the drive about the supported speeds. E.g. with a "16x" DVD-R
i get offered by an ASUS BW-16D1HT drive: 8x, 12x, 16x. No 4x.

The real speed on DVD-R depends on the write position. It increases on
the way to the rim of the medium. Full nominal speed is often reached
only at the very end of the burn run.


The fact that the medium did not stay appendable is surprising.
Maybe Brasero obeys that check-box only with data compositions but not
with burning of readily formatted filesystem images.

The lengthy log of such a Brasero run might give hints what Brasero planned
to do.


raleigh3 wrote:
>  R means that it can only be written to once.

But it is supposed to be writable on its yet unused area after a
burn program kept it appendable.

Theoretically a DVD-R can take 99 sessions. In practice this is hardly
achievable because a dozen unused MB remain between each session.
But 30 sessions of incremental backups are well realistic.

Have a nice day :)

Thomas

Thank you

---

### Post by scdbackup on 2018-03-20
Hi,

maybe you worry in vain just because of a misleading message by Brasero.

I thoroughly blanked a DVD-RW to make it resemble a blank DVD-R.
(Done by xorriso. There i know what it does.)
Then i used Brasero 3.11.4 to burn an ISO to it, having checked in sub-menu
"Properties" the line "Leave this disc open to add other files later".

The burn progress window indeed reported "Finalizing" when the burn run
was nearly completed.

But the resulting medium is not closed:
```

$ xorriso -outdev /dev/sr4 -toc
...
Media current: DVD-RW sequential recording
Media product: RITEKW04 , Ritek Corp
Media status : is written , is appendable
Media blocks : 145680 readable , 2123520 writable , 2298496 overall
TOC layout   : Idx ,  sbsector ,       Size , Volume Id
ISO session  :   1 ,         0 ,    131591s , PBOOT
Media summary: 1 session, 145680 data blocks,  285m data, 4148m free
Media nwa    : 174368s
$
$
$ dvd+rw-mediainfo /dev/sr4
...
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    2
 State of Last Session: empty
 "Next" Track:          2
 Number of Tracks:      2
...
READ TRACK INFORMATION[#1]:
 Track State:           complete incremental
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            145680*2KB
 Last Recorded Address: 145679*2KB
READ TRACK INFORMATION[#2]:
 Track State:           invisible incremental
 Track Start Address:   174368*2KB
 Next Writable Address: 174368*2KB
 Free Blocks:           2123520*2KB
 Track Size:            2123520*2KB
...
READ CAPACITY:          145680*2048=298352640

```

Brasero ejected the drive tray but complained about having failed
to do so. Then it reported the absent medium as blank DVD with 4.4 GB
free space ... urgh ...
... and i miserably fail to get to see the log which other people post
when they have problems with Brasero. So i don't even know whether it
used growisofs or libburn.

-----

Use one of the above tools to check your medium state.
The decisive text line with xorriso is:
```

Media status : is written , is appendable

```
and with dvd+rw-mediainfo:
```

 Disc status:           appendable

```


Have a nice day :)

Thomas

---

