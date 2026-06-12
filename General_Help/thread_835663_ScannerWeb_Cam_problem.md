---
title: "Scanner/Web Cam problem"
date: 2008-06-20
forum: General Help
---

### Post by sumone on 2008-06-20
Hi All

When using Xsane I get an error "Failed to open device v4l:/dev/video0:Invalid Argument. I have an Epson scanner and a Logitech webcam both USB.

The output from sane-find-scanner and scanimage -L follow:

$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x012e [EPSON Scanner]) at libusb:006:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
$ scanimage -L
device `v4l:/dev/video0' is a Noname UVC Camera (046d:0990) virtual device

Also v4l2 device info gives:
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
	driver                  : "uvcvideo"
	card                    : "UVC Camera (046d:0990)"
	bus_info                : "0000:00:1d.7"
	version                 : 0.1.0
	capabilities            : 0x4000001 [VIDEO_CAPTURE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
	index                   : 0
	name                    : "Camera 1"
	type                    : CAMERA
	audioset                : 0
	tuner                   : 0
	std                     : 0x0 []
	status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
	index                   : 0
	type                    : VIDEO_CAPTURE
	flags                   : 1
	description             : "MJPEG"
	pixelformat             : 0x47504a4d [MJPG]
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
	index                   : 1
	type                    : VIDEO_CAPTURE
	flags                   : 0
	description             : "YUV 4:2:2 (YUYV)"
	pixelformat             : 0x56595559 [YUYV]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
	type                    : VIDEO_CAPTURE
	fmt.pix.width           : 320
	fmt.pix.height          : 240
	fmt.pix.pixelformat     : 0x47504a4d [MJPG]
	fmt.pix.field           : NONE
	fmt.pix.bytesperline    : 0
	fmt.pix.sizeimage       : 102400
	fmt.pix.colorspace      : SRGB
	fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
	id                      : 9963776
	type                    : INTEGER
	name                    : "Brightness"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 128
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
	id                      : 9963777
	type                    : INTEGER
	name                    : "Contrast"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 32
	flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
	id                      : 9963778
	type                    : INTEGER
	name                    : "Saturation"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 32
	flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+0)
	id                      : 134217728
	type                    : INTEGER
	name                    : "Backlight Compensation"
	minimum                 : 0
	maximum                 : 2
	step                    : 1
	default_value           : 1
	flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+1)
	id                      : 134217729
	type                    : MENU
	name                    : "Power Line Frequency"
	minimum                 : 0
	maximum                 : 2
	step                    : 1
	default_value           : 2
	flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+2)
	id                      : 134217730
	type                    : INTEGER
	name                    : "Sharpness"
	minimum                 : 0
	maximum                 : 255
	step                    : 1
	default_value           : 224
	flags                   : 0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "UVC Camera (046d:0990)"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 0
	maxheight               : 0
	minwidth                : 48
	minheight               : 32

channels
ioctl VIDIOCGCHAN: Invalid argument

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
	brightness              : 32896
	hue                     : 0
	colour                  : 8224
	contrast                : 8224
	whiteness               : 0
	depth                   : 0
	palette                 : unknown

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 320
	height                  : 240
	chromakey               : 0
	flags                   : 0

Could someone help me fix this please?

Thanks

Dave J

---

### Post by paddy1978 on 2008-06-21
Hi,

Have you seen this page [https://help.ubuntu.com/community/ScanningHowTo]("https://help.ubuntu.com/community/ScanningHowTo")? Hopefully some of the suggestions there might work.

Just managed to get my Epson printer/scanner (DX5000) working following these steps (actually managed to get mine shared via a Debian server on the network and accessible to Ubuntu/Windows clients, so a slightly different set-up...)

Cheers,

Tom

---

