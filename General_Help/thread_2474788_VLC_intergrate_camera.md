---
title: "VLC intergrate camera"
date: 2022-05-07
forum: General Help
---

### Post by cam17 on 2022-05-07
When  I try to use the integrated camera in VLC it tries to use /dev/video or /dev/video1 which do not exist in Ubuntu. How can I get the proper device for my integrated camera?

---

### Post by HermanAB on 2022-05-08
Well, TIMTOWTDI.  You can read the VLC manuals, or you could make a soft link /dev/video to whatever your video device actually is.

---

### Post by cam17 on 2022-05-09
What is ubuntu default device location? this does not have ot do wiht VLC as other O.S. including other Linux have no problem displaying the device location.

---

### Post by HermanAB on 2022-05-10
Just list /dev:
$ ls /dev | less

---

### Post by cam17 on 2022-05-11
So which one is the built in camera?
autofs           loop10        null       tty19  tty57      ttyS8
block            loop11        nvme0      tty2   tty58      ttyS9
bsg              loop12        nvme0n1    tty20  tty59      udmabuf
btrfs-control    loop13        nvme0n1p1  tty21  tty6       uhid
bus              loop14        nvme0n1p2  tty22  tty60      uinput
cdrom            loop15        nvme0n1p3  tty23  tty61      urandom
char             loop16        nvme0n1p4  tty24  tty62      userio
console          loop17        nvme0n1p5  tty25  tty63      v4l
core             loop18        nvram      tty26  tty7       vboxdrv
cpu              loop19        port       tty27  tty8       vboxdrvu
cpu_dma_latency  loop2         ppp        tty28  tty9       vboxnetctl
cuse             loop20        psaux      tty29  ttyprintk  vboxusb
disk             loop21        ptmx       tty3   ttyS0      vcs
dm-0             loop22        ptp0       tty30  ttyS1      vcs1
dma_heap         loop23        pts        tty31  ttyS10     vcs2
dri              loop24        random     tty32  ttyS11     vcs3
drm_dp_aux0      loop25        rfkill     tty33  ttyS12     vcs4
drm_dp_aux1      loop26        rtc        tty34  ttyS13     vcs5
drm_dp_aux2      loop27        rtc0       tty35  ttyS14     vcs6
ecryptfs         loop28        sda        tty36  ttyS15     vcsa
fb0              loop29        sda1       tty37  ttyS16     vcsa1
fd               loop3         sg0        tty38  ttyS17     vcsa2
full             loop30        shm        tty39  ttyS18     vcsa3
fuse             loop31        snapshot   tty4   ttyS19     vcsa4
hpet             loop32        snd        tty40  ttyS2      vcsa5
hugepages        loop33        stderr     tty41  ttyS20     vcsa6
hwrng            loop34        stdin      tty42  ttyS21     vcsu
i2c-0            loop4         stdout     tty43  ttyS22     vcsu1
i2c-1            loop5         tpm0       tty44  ttyS23     vcsu2
i2c-2            loop6         tpmrm0     tty45  ttyS24     vcsu3
i2c-3            loop7         tty        tty46  ttyS25     vcsu4
i2c-4            loop8         tty0       tty47  ttyS26     vcsu5
i2c-5            loop9         tty1       tty48  ttyS27     vcsu6
i2c-6            loop-control  tty10      tty49  ttyS28     vfio
initctl          mapper        tty11      tty5   ttyS29     vga_arbiter
input            mcelog        tty12      tty50  ttyS3      vhci
kmsg             media0        tty13      tty51  ttyS30     vhost-net
kvm              mei0          tty14      tty52  ttyS31     vhost-vsock
lightnvm         mem           tty15      tty53  ttyS4      video0
log              mqueue        tty16      tty54  ttyS5      video1
loop0            net           tty17      tty55  ttyS6      zero
loop1            ng0n1         tty18      tty56  ttyS7      zfs

---

### Post by HermanAB on 2022-05-12
Look carefully and you will see /dev/video0

---

### Post by cam17 on 2022-05-12
That is VLC default /dev/video0 (I miss typed initially) but it cannot find the device. Is there a method to test?

---

### Post by cam17 on 2022-05-12
i should add chees app works and is able to find my integrated camera.

---

### Post by him610 on 2022-05-14
What is better than cheese?
```
guvcview &
```

---

### Post by HermanAB on 2022-05-15
You can also play the camera with ffplay or gst-play.  

For example: 
$ ffplay /dev/video0 
or with: 
$ gst-play-1.0 /dev/video0

The above is a good way to see any error messages, which may then tell you what exactly is not configured right.

---

### Post by cam17 on 2022-05-28
The problem is when VLC is installed the permissions for the camera are disabled by default.

---

