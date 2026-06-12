---
title: "32bit vs 24 bit color?"
date: 2006-10-04
forum: General Help
---

### Post by NoTiG on 2006-10-04
just wondering.... windows says that my desktop is running at 32 bit colors and in xorg all i see are entries up to 24bit. does anyone have 32 bit colors in linux??

---

### Post by Bokonon on 2006-10-04
Sounds like some MS marketing BS.

From the wikipedia....

Truecolor

Truecolor can frequently mimic many colors found in the real world, producing 16.7 million distinct colors. This approaches the level at which the human eye can distinguish colors for most photographic images, though image manipulation, some black-and-white images (which are restricted to 256 levels with Truecolor) or "pure" generated images may reveal the limitations.

    * 24-bit Truecolor uses 8 bits to represent red, 8 bits to represent blue, and 8 bits to represent green. 28 = 256 levels of each of these three colors can therefore be combined to give a total of 16,777,216 mixed colors (256 x 256 x 256). Twenty-four-bit color is referred to as "millions of colors" on Macintosh systems.

[edit]

32-bit color

"32-bit color" is a misnomer when regarding display color depth. A common misconception is that 32-bit color produces 4,294,967,296 distinct colors.

In reality, 32-bit color actually refers to 24-bit color (Truecolor) with an additional 8 bits either as empty padding space or to represent an alpha channel. Considering red, green, and blue use the same amount of bits for their respective color (with the exception of 16-bit color), the total bits used will be a multiple of 3: like 15-bit color (5 bits each) and 24-bit color (8 bits each). The reason for using empty space is that all but the newest modern computers process data internally in units of 32 bits; as such, using this amount for each pixel can allow optimizations.

---

### Post by NoTiG on 2006-10-04
ah. think i knew this a long time ago but forgot. probably should have searched wiki instead of the forums :P

nice computers you got there!

---

### Post by Morot313 on 2008-03-13
I guess you do not know what you are talking about.

When you refer to Linux, you actually mean Xorg or the X Window System.

It mentions 24-bit which is essentially the same as 32-bit.
Vista and Mac OS X uses 24-bit color depth (bits per pixel) too.

32-bit color is a misnomer.

"Truecolor" is 24-bit.

[http://en.wikipedia.org/wiki/Color_depth#32-bit_color](http://en.wikipedia.org/wiki/Color_depth#32-bit_color)

---

