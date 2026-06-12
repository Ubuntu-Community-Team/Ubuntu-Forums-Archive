---
title: "camserv bttv help"
date: 2005-04-21
forum: General Help
---

### Post by clarkee on 2005-04-21
I'm using a bttv card on linux (abuntu 5.04).  Using something like
tvtime i can see composite2 and the video feed is fine.

i have recently installed camserv, but i cannot get it to work.

the error i recieve is:

 (V4L) mmap: Invalid argument

Do you have any clue what is going on?  I'm not a power user, but I know
enough to get by.  Any advice you have would be greatly appreciated.

James Clarke.

my config goes like this:



[video_basic]
path		/usr/lib/camserv/libvideo_basic.so.0

[video_v4l_bttv]
path		/usr/lib/camserv/libvideo_v4l.so.0
device_path	/dev/video0
port		2
mode		3
#frequency	74.43
color		30000
hue		30000
contrast	30000
brightness	30000
whiteness	30000
autobright	1
brightmean      128
brightx1	0
brighty1	320
brightx2	0
brighty2	240

[jpg_filter]
path            /usr/lib/camserv/libjpg_filter.so.0
quality		30

[socket]
listen_port		1337
max_frames		0
max_bytes		0
max_seconds		0

[filters]
num_filters   	      	1
#filter0_section		time_stamp
filter0_section		jpg_filter

[video]
video_section		video_v4l_bttv
width			320
height			240
maxfps                  10
memhack			1

[main]
#output_snapfile		foo.jpg
#output_presnaps		100

---

### Post by steph291 on 2008-06-13
Hi,

I have the same problem :(
I need 1 frame per second in a web page
and camserv is doing fine with my usb quickcam
but with my bt848 capture card, I have the same error
as you.

I disconnected my usb cam and no show, the same error :(
It's working fine with xawtv for the two cameras and
I can have 2 instances of xawtv on both webcam running at
the same time.

Let's say I prefer my 3com bigpicture than my quickcam
better quality of image but it's not working anymore :(

I suspect it's a problem with the software, it
dont likes v4l2 or kernel 2.6, i'm looking into this
problem for 6 months, nothing in the internet/forum
could solve the problem

please people, do something !
thanks

---

