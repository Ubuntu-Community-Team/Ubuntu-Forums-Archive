---
title: "Xsane scanning"
date: 2007-07-23
forum: General Help
---

### Post by LinuxBob on 2007-07-23
I am trying to scan some receipts using Xsane however it thinks my Happuage TV tuner is the preferred scanning device. It is not, I have a networked HP 6110 All in One.

How do I change the device from which I want to scan? The help on Xsane is weak , this is a fundamental procedure and should be straight forward.

Thanks

---

### Post by Gruelius on 2007-07-23
im not an Xsane expert however we can all benifit from some more information. Is the scanner shared via a serving pc or is it self serving (plugs into network)?

Im not on my ubuntu box atm so i cant be much of a help, but you may want to look at adding the device locally before you can select it. If the device is added prowl around Xsane or have a look at the configuration files in the /etc/ or ~/. folders

good luck

---

### Post by LinuxBob on 2007-07-23
The HP 6110 All in One printer/copier/scanner is networked via a USB print server, Netgear PS 121 (6110 into USB of PS 121, RJ 45 from PS 121 to router).  The printer works, as do two other networked printers.

---

### Post by LinuxBob on 2007-07-24
Nobody knows how to do this?

---

### Post by expatCM on 2007-09-27
If you power on your scanner before you launch xsane there should be a window which appears when you launch xsane asking you to select which device.  This window also lets you select the default device .......

---

### Post by gobbles414 on 2007-09-27
Hi LinuxBob,

Have we met in another thread...? Anyway, I recommend forgetting xsane and using a program called [gscan2pdf]("http://gscan2pdf.sourceforge.net") instead. The gscan program  is a much more powerful application with a MUCH MUCH MUCH better interface than xsane. This includes an easier way to select scanning devices than in xsane. I personally installed all of the extras recommended by gscan as well as sane-utils and libsane-extras (libsane-extras might help if you still want to use xsane). I also followed the instructions on the gscan website so that the program is recognized in the synaptic package manager and updates are available in the update manager.

I cannot garuntee that scanning will work since you are using a print server. But gscan2pdf is work a try.

---

### Post by expatCM on 2007-09-27
I will also comment that gscan2pdf is a VERY NICE program.  I so wish that I could use it but my scanner has some challenges when it comes to working with the program :(

---

### Post by gobbles414 on 2007-09-27
expatCM,

What kind of problems are you experiencing? I've been using gscan2pdf for several months and I might be able to help.

---

### Post by expatCM on 2007-09-27
The scanner is an HP3970 which works with other programs.  With earlier versions of gscan2pdf only the first page was scanned, all other pages were black.  The latest release however will not even run the scanner .....

For your interest here is the output of gscan2pdf --debug

```
~$ gscan2pdf --debug
gscan2pdf 0.9.16
Using en_US.UTF-8 locale
Gtk2-Perl version 1.140
Built for 2.10.9
Running with 2.10.11
$VAR1 = {
          'no-blackfilter' => '',
          'ocr panel' => '529',
          'frontend' => 'scanimage',
          'mode' => 'Color',
          'no-border-scan' => '',
          'window_maximize' => '1',
          'no-blurfilter' => '',
          'white-threshold' => '0.9',
          'y' => '0',
          'layout' => 'single',
          'cwd' => '/home/peter',
          'OCR on scan' => '',
          't' => '0',
          'Paper size' => 'Custom',
          'Page range' => 'all',
          'no-deskew' => '',
          'window_height' => '692',
          'startup warning' => '',
          'no-grayfilter' => '',
          'pages to scan' => '1',
          'no-border-align' => '',
          'resolution' => '300',
          'unpaper on scan' => '',
          'source' => 'Flatbed',
          'x' => '0',
          'downsample dpi' => '150',
          'window_width' => '1024',
          'window_x' => '0',
          'deskew-scan-direction' => 'left,right',
          'window_y' => '0',
          'thumb panel' => '128',
          'enable options' => '1',
          'version' => '0.9.16',
          'device' => 'hp3900:libusb:005:004',
          'no-noisefilter' => '',
          'l' => '0',
          'no-mask-scan' => '',
          'downsample' => '',
          'black-threshold' => '0.33',
          'restore window' => '1'
        };
Found PDF::API2
Found Image::Magick
Found ImageMagick
Found xdg-email
Found gocr
Found cjb2 (djvu)
Found unpaper
Found libtiff
scanimage --formatted-device-list="'%i','%d','%v %m'
" 2>/dev/null
Forked PID 7639
Waiting to reap process at /usr/bin/gscan2pdf line 2732.
Reaped PID -1
'0','hp3900:libusb:005:004','Hewlett-Packard RTS8822 chipset based'
scanimage --help --device-name='hp3900:libusb:005:004' --mode='Color'
Forked PID 7642
Waiting to reap process at /usr/bin/gscan2pdf line 3733.
Reaped PID -1
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), and %i (index number)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase number in filename by an amount of #
    --batch-double         increment page number by two for 2sided originals
                           being scanned in a single sided scanner
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size          change default input buffersize
-V, --version              print version information

Options specific to device `hp3900:libusb:005:004':
    -l 0..220mm (in steps of 1) [220]
        Top-left x position of scan area.
    -t 0..300mm (in steps of 1) [300]
        Top-left y position of scan area.
    -x 0..0mm (in steps of 1) [0]
        Width of scan-area.
    -y 0..0mm (in steps of 1) [0]
        Height of scan-area.
    --resolution 75|100|150|200|300|600|1200|2400dpi [75]
        Sets the resolution of the scanned image.
    --red-gamma-table 0..65535,...
        Gamma-correction table for the red band.
    --green-gamma-table 0..65535,...
        Gamma-correction table for the green band.
    --blue-gamma-table 0..65535,...
        Gamma-correction table for the blue band.
    --source Flatbed|Slide|Negative [Flatbed]
        Selects the scan source (such as a document-feeder).
    --mode Color|Gray|Lineart [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --depth 8|16bit [8]
        Number of bits per sample, typical values are 1 for "line-art" and 8
        for multibit scans.
    --threshold 0..255 [inactive]
        Select minimum-brightness to get a white point

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    hp3900:libusb:005:004
$VAR1 = {
          'source' => {
                        'tip' => 'Selects the scan source (such as a document-feeder).',
                        'default' => 'Flatbed',
                        'values' => 'Flatbed|Slide|Negative'
                      },
          'threshold' => {
                           'tip' => 'Select minimum-brightness to get a white point',
                           'default' => 'inactive',
                           'values' => '0..255'
                         },
          'mode' => {
                      'tip' => 'Selects the scan mode (e.g., lineart, monochrome, or color).',
                      'default' => 'Color',
                      'values' => 'Color|Gray|Lineart'
                    },
          'resolution' => {
                            'tip' => 'Sets the resolution of the scanned image.',
                            'default' => '75',
                            'values' => '75|100|150|200|300|600|1200|2400dpi'
                          },
          'depth' => {
                       'tip' => 'Number of bits per sample, typical values are 1 for "line-art" and 8 for multibit scans.',
                       'default' => '8',
                       'values' => '8|16bit'
                     }
        };
$VAR1 = {
          'source' => 'Flatbed',
          'l' => '0',
          'y' => '0',
          'mode' => 'Color',
          'resolution' => '300',
          'x' => '0',
          't' => '0'
        };
scanimage --device-name='hp3900:libusb:005:004' --mode='Color' --source='Flatbed' -l 0 -y 0 --resolution='300' -x 0 -t 0 --batch --batch-count=1
Forked PID 7669
Unknown message: scanimage: sane_start: Invalid argument
Waiting to reap process at /usr/bin/gscan2pdf line 3278.
Reaped PID 7669
```

and scanimage --help
```

 scanimage --help 
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), and %i (index number)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase number in filename by an amount of #
    --batch-double         increment page number by two for 2sided originals
                           being scanned in a single sided scanner
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size          change default input buffersize
-V, --version              print version information

Options specific to device `hp3900:libusb:005:004':
    -l 0..220mm (in steps of 1) [220]
        Top-left x position of scan area.
    -t 0..300mm (in steps of 1) [300]
        Top-left y position of scan area.
    -x 0..0mm (in steps of 1) [0]
        Width of scan-area.
    -y 0..0mm (in steps of 1) [0]
        Height of scan-area.
    --resolution 75|100|150|200|300|600|1200|2400dpi [75]
        Sets the resolution of the scanned image.
    --red-gamma-table 0..65535,...
        Gamma-correction table for the red band.
    --green-gamma-table 0..65535,...
        Gamma-correction table for the green band.
    --blue-gamma-table 0..65535,...
        Gamma-correction table for the blue band.
    --source Flatbed|Slide|Negative [Flatbed]
        Selects the scan source (such as a document-feeder).
    --mode Color|Gray|Lineart [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --depth 8|16bit [8]
        Number of bits per sample, typical values are 1 for "line-art" and 8
        for multibit scans.
    --threshold 0..255 [inactive]
        Select minimum-brightness to get a white point

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    hp3900:libusb:005:004


```

I am open to suggestions but buying a new scanner is not one of them :)

---

### Post by gobbles414 on 2007-09-28
expatCM,

Have you installed all of the extras recommend by gscan2pfd as well as packages sane-utils and libsane-extras? The names of the recommended packages can be easily viewed from within synaptic if you follow directions on the gscan2pdf website. You might also try searching for *hp* in synaptic to see if any helpful drivers are available.

Another tip to try is manually adding details about your scanner into the appropriate file. The file to edit is different depending on the brand of your scanner. Look for threads discussing the *sane-find-scanner* command along with HP scanners to learn which file to edit.

---

### Post by expatCM on 2007-09-28
Yes, I installed everything needed and everything recommended.

The scanner is installed and does work with other applications, it just having problems with gscan2pdf.

---

### Post by JeffreyRatcliffe on 2007-10-09
> **expatCM said:**
> ```
scanimage --device-name='hp3900:libusb:005:004' --mode='Color' --source='Flatbed' -l 0 -y 0 --resolution='300' -x 0 -t 0 --batch --batch-count=1
Forked PID 7669
Unknown message: scanimage: sane_start: Invalid argument
Waiting to reap process at /usr/bin/gscan2pdf line 3278.
Reaped PID 7669
```

Either scanimage or SANE is having a problem with your scanner. gscan2pdf relies on either scanimage or scanadf. I would first suggest trying scanadf under Edit/Frontend.

If you get the invalid argument error message with scanadf as well, it looks as though the problem is SANE, which you might not be able to do much about.

Otherwise, starting from the ```
scanimage --device-name='hp3900:libusb:005:004' --mode='Color' --source='Flatbed' -l 0 -y 0 --resolution='300' -x 0 -t 0 --batch --batch-count=1
``` call, take away options until scanimage actually produces a sensible results.

---

### Post by expatCM on 2007-10-11
think I will wait until I have Gutsy installed and then explore more.  Thank you for your suggestions.

---

