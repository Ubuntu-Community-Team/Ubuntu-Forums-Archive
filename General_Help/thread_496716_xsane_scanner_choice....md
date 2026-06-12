---
title: "xsane scanner choice..."
date: 2007-07-09
forum: General Help
---

### Post by bazzer on 2007-07-09
Hi all
I need to get a scanner, and I'm a little confused by the current situation as regards support for them. I perceive it as 'New (ie on the market now) scanners are not yet supported' and 'some older scanners work with some degree of fiddling'.

So, how do I purchase one? Do I buy one and wait until someone decides to write (backwards engineering or otherwise) a driver for it, or are my choices limited to ebay for second-hand equipment...?

Anyone's thoughts please??:popcorn:

---

### Post by Vajra Vrtti on 2007-07-09
I would first check supported scanners at [SANE]("http://www.sane-project.org/").

---

### Post by bazzer on 2007-07-11
Well I thought it's only polite to say thanks Vajra - that was what I had done but after clicking the link, I saw there is a handy little search engine for supported devices. I looked at some budget scanners from ebuyer and saw the Canon CanoScan LiDE25 was supported at a 'Good' level by the Mustek backend and no separate PSU - it runs off the USB power, so I got one....

So it arrived this morning and I plugged it in. Initial thoughts were that I had a DOA unit, as it wouldn't do anything at all, but with a little perseverance, I worked out the USB sockets on the back of my PC had a higher mA output than the front ones (where I had connected it) and it finally did something in SANE. However, not all was good, the scan it produced was black and no movement from the scanner was attempted. But then, I stumbled over [this ]("http://liltux.wordpress.com/2007/05/23/using-a-canoscan-lide-25-with-sane-and-ubuntu/") page and advised to do this:
```
scanimage -L
```
and this:
```
scanimage --format=tiff --mode=Gray --depth=16 --resolution=100dpi -l 0 -t 0 -x 215 -y 215 >> test
```
which worked....

So then, I wanted the scanner buttons to work. I'm not remotely interested in fiddling with the image before saving it, I simply want to be able to hit a button and see a jpeg appear on my desktop. I googled and found [this]("http://www.linux.com/feature/59138") page which almost worked, but not quite. I had to fiddle a little with the buttonpressed.sh file and install imagemagick and then all was perfect. :)

For those that are still awake and with me, here is my buttonpressed.sh:
```
#!/bin/sh

# daemon's name
DAEMON=scanbuttond

# securely create temporary file to avoid race condition attacks
TMPFILE=`mktemp /tmp/$DAEMON.XXXXXX`

# lock file
LOCKFILE="/tmp/$DAEMON.lock"

# device name
DEVICE="$2"

# destination of the final image file (modify to match your setup)
DESTINATION="/home/barry/Desktop/scanned_image.jpg"

# remove temporary file on abort
trap 'rm -f $TMPFILE' 0 1 15

# function: create lock file with scanbuttond's PID
mk_lock() {
	pidof $DAEMON > $LOCKFILE
}

# function: remove temporary and lock files
clean_up () {
	test -e $LOCKFILE && rm -f $LOCKFILE
	rm -f $TMPFILE
}

# function: check if lock file exists and print an error message with zenity (if it's installed)
chk_lock() {
	if [ -e $LOCKFILE ]; then
		if [ -x /usr/bin/zenity ]; then
			zenity --display :0.0 --title="Scanbuttond" --error \
			--text="Another scanning operation is currently in progress."
		fi
		exit 1
	fi
}

# function: the actual scan command (modify to match your setup)
scan() {
	scanimage --mode Color --resolution=100dpi --depth=16 -l 0 -t 0 -x 215 -y 297 > $TMPFILE
}

case $1 in
	1)
	   # button 1 (scan): scan the picture & save it as $DESTINATION
	   chk_lock; mk_lock; scan; convert $TMPFILE -quality 85 -quiet $DESTINATION; clean_up
#scanimage --format=tiff --mode=Gray --depth=16 --resolution=100dpi -l 0 -t 0 -x 215 -y 215 >> $DESTINATION

	   ;;
	2)
	   # button 2 (copy): scan the picture, convert it to postscript and print it
	   chk_lock; mk_lock; scan; convert $TMPFILE ps:- | lpr; clean_up
	   ;;
	3)
	   # button 3 (mail): scan the picture, save it as $DESTINATION and send it as an e-mail
	   # attachment with Evolution
	   chk_lock; mk_lock; scan; convert $TMPFILE -quality 85 -quiet $DESTINATION
	   evolution --display=:0.0 "mailto:?attach=$DESTINATION"; clean_up
	   ;;
	4)
	   # button 4 (web): unconfigured
	   echo "button 4 has been pressed on $2"
	   ;;
esac
```

---

### Post by bratliff on 2007-08-10
Is your canoscan lide25 working for you now? Did you do all the stuff on this link How to configure a scanner's buttons on Linux [http://www.linux.com/feature/59138](http://www.linux.com/feature/59138) ?

Ratliff

---

### Post by bazzer on 2007-08-13
er... yes thanks, see above post!

---

