---
title: "Ubuntu and JVC .mod files"
date: 2006-08-07
forum: General Help
---

### Post by Jonathan Métillon on 2006-08-07
Hi,

I own a [JVC Everio GZ-MC200]("http://reviews.cnet.co.uk/camcorders/0,39029967,39189058,00.htm") that writes video files directly on a Microdrive.

These files use a .mod filename suffix and are in fact [MPEG-2 Program Stream]("http://en.wikipedia.org/wiki/MPEG-2") video with [AC-3]("http://en.wikipedia.org/wiki/Dolby_Digital") audio. They should be DVD compliant.

The USB device is recognized and I can import the files. I can read them with Totem and MPlayer. But as you can see with the attached screenshot from Totem, the video looks interlaced/scanlined. How can I prevent this? :confused: 

And of course I'd want to edit them. This is the last step for me to fully switch from Windows to Ubuntu :KS 

I tried [Kino]("http://en.wikipedia.org/wiki/Kino_%28software%29") and [PiTiVi]("http://en.wikipedia.org/wiki/PiTiVi"). PiTiVi loads them but I can't do nothing in the timeline. The scenes seem like frozen. And Kino won't even import them.

I also tried [Avidemux]("http://en.wikipedia.org/wiki/Avidemux") and I was able to read the files, cut them, and encode with Xvid4 and H263. (The interlaced look was still present).

I'd want to try [Cinelerra]("http://en.wikipedia.org/*wiki/Cinelerra") but I was not able to install it following the instructions [here.]("http://www.kiberpipa.org/~gandalf/ubuntu/README") Synaptic said that:

```
Depends: libiec61883-0  but it is not installable
Depends: libquicktimehv but it is not going to be installed
Depends: libraw1394-8  but it is not installable
Depends: libquicktimehv but it is not going to be installed
```

So, does someone successfully edited these .mod files under Linux? :-k 

Thanks for reading me!

---

### Post by Jonathan Métillon on 2006-08-07
I just noticed this [related thread.]("http://ubuntuforums.org/showthread.php?t=122652")

But it does not bring any answer and it is almost 7 months old, so I hope it does not mean that noone knows how to work with these files :???:

---

### Post by Lunar_Lamp on 2006-08-07
I believe that cineralla is available for dapper.  If you add the followin got your /etc/apt/sources.list

```
## cinelerra
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./

```

Just "sudo aptitude install cinelerra".  It may be an idea to check out the cineralla forums (I'm sure there are some somewhere) if you don't get a fast answer.

---

### Post by Jonathan Métillon on 2006-08-07
> **Lunar_Lamp said:**
> I believe that cineralla is available for dapper.

Thank you Lunar_Lamp! But as I said that's what I've done: I followed Jure Cuhalev's instructions [URL="http://www.kiberpipa.org/~gandalf/ubuntu/README"]here
[/URL]. So yes I added the repositories and tried to install using Synaptic. And I had an error that some files needed can't be found in any repositories. That's where I gave up ](*,)

---

### Post by ddennedy on 2006-08-08
You can get the libiec61883 package from [www.debian-multimedia.org](www.debian-multimedia.org) (Marillat).

Regarding interlace, you do not want to get rid of it if you are planning to make it into a DVD. Just because it looks bad on your computer, particularly when stopped, does not mean it will look bad when properly played back. It is the job of the player to do deinterlace if appropriate (e.g., on SD TV it looks better interlaced). You did say the mpeg-2 was suitable for DVD, then you do not want to reencode it if at all possible. But you best check the datarate of the camera's output before claiming DVD compliance. If it is over 9 mbps, then you could run into problems.

If you are encoding to a format suited more for distribution over the internet and most likely played on computer, then you do want to apply a deinterlace filter. Things like avdemux2, mencoder2, and ffmpeg supply deinterlace options.

---

### Post by ddennedy on 2006-08-08
FYI, for lossless editing, I hear gopchop works [http://gopchop.sourceforge.net/](http://gopchop.sourceforge.net/)

---

### Post by hfdragon on 2006-12-06
I'm interested in this problem since I consider buying such a video camera (JVc Eviro).

Has anyone managed to read these .mod files with a program and write them to a DVD ?

---

### Post by Jonathan Métillon on 2006-12-07
Hi hfdragon,

I think the current generation of Everio is not that good. You should wait for the new [Everio HD]("http://crave.cnet.co.uk/camcorders/0,39029423,49284083,00.htm"), or look at Sony with the [DCR-SR100]("http://www.camcorderinfo.com/content/Sony-DCR-SR100-Camcorder-Review.htm") or [HDR-SR1]("http://www.camcorderinfo.com/content/Sony-HDR-SR1-Camcorder-Review.htm"). It supports [16:9]("http://en.wikipedia.org/wiki/Aspect_ratio_%28image%29#16:9_standard")   aspect ratio, [Full HD 1080p]("http://en.wikipedia.org/wiki/1080p") with [HDMI]("http://en.wikipedia.org/wiki/HDMI")   output (HDR-SR1 only), touch-screen control and jog dial.

But you may run in the same kind of issue I had with the .MOD files from the Everio: the Sony uses a new file format [AVCHD]("http://en.wikipedia.org/wiki/AVCHD"), which seems to be [MPEG-2 PS]("http://en.wikipedia.org/wiki/Program_stream")   with [H.264]("http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC")   video.

Also note that the [GZ-MC200E]("http://www.camcorderinfo.com/content/JVC-GZ-MC200-Camcorder-Review.htm")   has a few issues, like very slow cold start, very low light sensitivity, bad stabilizer, bad controls and menus, etc...

*BUT*, it produces very nice video files on a hard drive, makes good photos and is very tiny :-) So I love it anyway. And that's why I kept struggling with .MOD files and Linux, and here is my little guide.

[SIZE=4]**Import**[/SIZE]

.MOD files are just MPEG-2 PS files, which contains [MPEG-2 video]("http://en.wikipedia.org/wiki/MPEG-2#DVD")   (DVD profile) and [AC-3]("http://en.wikipedia.org/wiki/Dolby_Digital") audio. Ubuntu understand MPEG-2 out of the box, so changing the extension of your files for .mpg will enable playing in your prefered media player when double-clicking a file (instead of saying it's an Amiga audio file), and preview thumbnails in Nautilus.

So you just plug-in the USB cable and it is recognized as an external hard drive, mounted on /media/usbdisk. When you have moved all my files from the Everio to the computer, you can change all files extension with this simple line added to your ~/.bashrc file:

```
function mod2mpg() { find . -type f -name *.MOD -exec sh -c 'mv "{}" `dirname "{}"`/`basename "{}" | sed "s/MOD/mpg/"`; echo {}' \;;  }
```Then type ***mod2mpg*** in the directory where you moved your files.

[SIZE=4]**Edit**[/SIZE]

Now with video editing. If you just want to author a video DVD without editing, you should be able to use your files directly, theMPEG-2 DVD profile is meant for that. But I never did it, so you should [look by yourself]("http://www.google.com/search?q=Ubuntu+DVD+authoring").

I chose [Kino]("http://en.wikipedia.org/wiki/Kino_%28software%29")   for my video editing. It is a bit weird to use when you are used to [PowerDirector]("http://en.wikipedia.org/wiki/CyberLink"), the Windows software bundled with the Everio. But if you take the time to read the doc and memorize the Vim-like keyboard shortcuts, it becomes really easy and efficient.

Before Kino I tried [Cinelerra]("http://en.wikipedia.org/wiki/Cinelerra"). Apart the fact that it was not easy to install, I can't cope with the UI. It is awful and not intuitive. Then I tried [Pitivi]("http://en.wikipedia.org/wiki/Pitivi")  , which as a good UI, but it's all it has. And I found [Diva]("http://www.diva-project.org/"), which looks very promising, but the website was down every time I wanted to get it from the website, and it is not available in Ubuntu depots.

The main drawback in Kino is that it's meant for DV. And It really doesn't support any other video file. So I have to first transcode all my MPEG-2 files to DV. Here is a [Ruby]("http://en.wikipedia.org/wiki/Ruby_%28programming_language%29")   script I wrote:

```
#!/usr/local/bin/ruby -w

require 'optparse'

OPTIONS = {}
OptionParser.new do |opts|
  opts.banner = <<EOUSAGE
Usage: #{File.basename($0)} [OPTION]... DIRECTORY
Transcode to DV all JVC Everio video files.
MPEG-2 PS is detected so the file extension maybe anything, like .MOD or .mpg.
EOUSAGE

  opts.on("-r", "--recursive", "Scan directories recursively") do |v|
    OPTIONS[:recursive] = v
  end

  opts.on("-h", "--help", "Show this message") do
    puts opts
    exit
  end
end.parse!

if ARGV[0].nil?
  puts <<EOERROR
#{File.basename($0)}: missing directory operand
Try `#{File.basename($0)} --help' for more information.
EOERROR
  exit
else
  dir = File.expand_path ARGV[0]
end

test = `which ffmpeg`
if test.empty?     
  puts <<EOERROR
#{File.basename($0)}: FFmpeg not found!
FFmpeg must be installed. Go to http://ffmpeg.mplayerhq.hu/ for more information.
EOERROR
  exit
end

def scan(dir, counter)
  entries = Dir.entries(dir)
  2.times { entries.shift }
  entries.each do |entry|
    entry = "#{dir}/#{entry}"
    if File.directory? entry
      if OPTIONS[:recursive]
        scan(entry, counter)
      end
    elsif Video.is_mpeg2_file? entry
      video = Video.new(entry)
      if video.to_cropped_dv
        counter.increment
      end
    end
  end
end

class Counter
  attr_writer :value

  def initialize
    @value = 0
  end

  def value
    @value
  end

  def increment
    @value += 1
  end
end

class Video
  attr_reader :path, :output_path
  MOD_HEADER = "\000\000\001\272D\000\004\000\004\001"

  def initialize(path)
    @path = path
    @output_path = build_output_path
  end

  def self.is_mpeg2_file?(path)
    header = File.open(path) { |f| f.read(10) }
    header.eql? MOD_HEADER
  end

  def to_cropped_dv
    puts "Transcoding #{path}..."
    if File.exists? output_path
      puts "File exists, skipped."
      result = false
    else
      `ffmpeg -i #{path} -croptop 84 -cropbottom 84 -aspect 16:9 -deinterlace -target dv #{output_path} >/dev/null 2>&1`
      result = true
    end
    result
  end

private
  def build_output_path
    dirname = File.dirname(path)
    output_dir = "#{dirname}/dv"
    unless File.exists? output_dir
      Dir.mkdir output_dir
    end
    "#{output_dir}/#{dv_basename}"
  end

  def dv_basename
    basename = File.basename(path).split(".")
    if basename.length > 1
      basename.pop
    end
    basename[0] = File.mtime(path).strftime("%Y-%m-%d-%H-%M-").to_s + basename[0]
    basename << "dv"
    basename.join(".")
  end
end

subdir = " and subdirectories" if OPTIONS[:recursive]
puts "Transcoding to DV all JVC Everio MPEG-2 files in #{dir}#{subdir}..."

counter = Counter.new
scan(dir, counter)

if counter.value > 0
  puts "#{counter.value} files transcoded."
else
  puts "No file transcoded."
end
```It detects all Everio video files in directory (should the extension be .MOD or .mpg, or else), and sub-directories if -r option is passed, and transcode them to DV. In the same time it crops them so they use a 16:9 ratio instead of the original 4:3. If you don't want that, just remove ***-croptop 84 -cropbottom 84 -aspect 16:9*** from the [FFmpeg]("http://en.wikipedia.org/wiki/FFmpeg") command.

Just copy this code to an empty file named transcode.rb and make it executable. Then link it from the bin directory, ie:

```
ln -s /home/john/scr/transcode.rb /bin/transcode
```Also note that the shebang line (the first line that starts with #!) must match your ruby executable path. If you are not sure, type

```
which ruby
```Then you will be able to transcode all files in current directory and all sub-directories, by typing:

```
transcode . -r
```When you have transcoded you .MOD files, you can now import the DV files in Kino. Just open Kino, type CTRL+o to open the first file, then type :a to add files. [Click here]("http://kinodv.org/article/archive/13/")   to learn more.

[SIZE=4]**Export**[/SIZE]

Now that you've edited your video, you'll want to create a DVD. I think you should go to the Export tab, then the MPEG tab, and play with the settings. Choose DVD in the File format menu. Then press the Export button at the bottom of the window. Then you can use the exported MPEG-2 in your DVD authoring software you found sooner ;-)

For me it's the Other tab I use. I only export videos for my website. So I have created a custom export script in /usr/share/kino/scripts/exports. It contains two Ogg Theora/Vorbis profiles: High Quality (720x408)and Broadband (480x272, 1000 Kbps). The first is just the same resolution as the original DV, for the archives, and the second is to be [embedded]("http://www.htmlhelp.com/reference/html40/special/object.html")   in a web page as [progressive download]("http://www.streamingmedia.com/article.asp?id=8456"). Note that 480x272 is the [PSP]("http://en.wikipedia.org/wiki/PlayStation_Portable")   resolution.

Here is the source of the export script:

```
#!/bin/sh
# written by jan gerber <j@v2v.cc>
# profiles added by Dan Dennedy
# customized for my use by Jonathan Métillon

usage()
{
    # Title
    echo "Title: Ogg Theora (ffmpeg2theora) (Customized)"

    # Usable?
    which ffmpeg2theora > /dev/null
    [ $? -eq 0 ] && echo Status: Active || echo Status: Inactive

    # Type
    echo Flags: single-pass file-producer
    
    # Profiles
    echo "Profile: High Quality (720x408)"
    echo "Profile: Broadband Quality (480×272, 1000 Kbps)"
}

execute()
{
    # Arguments
    normalisation="$1"
    length="$2"
    profile="$3"
    file="$4"
    project="$5"

    # generate filename if missing
    [ "x$file" = "x" ] && file="kino_export_"`date +%Y-%m-%d_%H.%M.%S`

  # Create metadata options
  artist=`awk '/artist="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /artist=/) z = y + 1; print x[z]; exit}' "$project"`
  title=`awk '/title="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /title=/) z = y + 1; print x[z]; exit}' "$project"`
  date=`awk '/date="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /date=/) z = y + 1; print x[z]; exit}' "$project"`
  location=`awk '/location="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /location=/) z = y + 1; print x[z]; exit}' "$project"`
  license=`awk '/license="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /license=/) z = y + 1; print x[z]; exit}' "$project"`


    # Run the command
    case "$profile" in 
        "0" )     ffmpeg2theora -f dv -x 720 -y 408 -d -v 10 -a 10 -H 48000 --optimize \
                --artist "$artist" --title "$title" --date "$date" --location "$location" --license "$license" \
                -o "$file".ogg - ;;
        "1" )     ffmpeg2theora -f dv -x 480 -y 272 -d -v 5 -V 1000 -a 3 -A 64 -H 44100 --optimize \
                --artist "$artist" --title "$title" --date "$date" --location "$location" --license "$license" \
                -o "$file".ogg - ;;
    esac
}

[ "$1" = "--usage" ] || [ -z "$1" ] && usage "$@" || execute "$@"
```So to conclude, these .MOD files can be used under Linux with no real pain. You just need extra time to convert the files to DV if you want to use Kino. Or another video editing software. The point is to use FFmpeg to convert the files to a format your software will be able to understand. The good point with DV it that you won't loose much quality in the process. 

My hope is that Diva will soon be available for Ubuntu, and will support MPEG-2/AC3 files out of the box :-D

---

### Post by Jonathan Métillon on 2006-12-27
Also note that if you want to use the ***--artist "$artist" --title "$title" --date "$date" --location "$location" --license "$license"*** options, you should set the values in your Kino project savefile. Which is just a [SMIL]("http://en.wikipedia.org/wiki/Synchronized_Multimedia_Integration_Language") file.

Open your savefile (ie: myproject.smil) in a text editor and edit only the first sequence. In the opening tag, add the attributes you need, like:

```
<seq artist="Jonathan Métillon"
  title="Chloë assise sur le lit"
  date="2006-11-30 10:51"
  location="France"
  license="Creative Commons Attribution-Share Alike http://creativecommons.org/licenses/by-sa/2.5/">
```

---

### Post by zhkent on 2007-05-15
Jonathan,
I am trying to edit the .mod files for use on a web site.  I keep the video length 1 to 3 minutes, and need to keep the file size reasonable.
I managed to edit and save a file in kino but it is huge for a web site.

Kent

---

### Post by Jonathan Métillon on 2007-05-15
Hi Kent,

Is there a question in your message?

About the size, well my last test was a 21 MB MPEG-2 video. Transcoded to DV, it inflated to 121 MB. Then after exporting to Ogg Theora/Vorbis, it weights only 4 MB (using my "Broadband Quality" settings).

I find that reasonable, if your target audience is using broadband connections (cable/DSL).

The final weight of your video will not only depends on its codec, resolution and bandwidth, but also on the content: if it's just a unique scene of a blue sky with slowly passing clouds, the video can be compressed a lot. But if it contains a lot of scenes with fast paced action, this will require a lot of key frames and will be much harder to compress.

Actually, you have to think of your bandwidth while doing the shoot: avoid movements like traveling or zoom. Try to stay steady at most, the best is to use a tripod. And if you have to shoot some action, then try not to be too close. For example, if you are filming a soccer match, instead of zooming the ball and moving the focus from player to player, try to get a larger view, so you can get the action as a whole, with more players in the view field, and move only when the action is going to another part of the terrain. Like that, their will be less pixels updated between frames, and it will be easier to compress.

---

### Post by zhkent on 2007-05-15
Jonathan,
Thank you very much for the response to a not so well worded post.:) 
What I want to do is upload short clips, keeping them as small as possible.  I was editing in cyberlink and saving as .wmv files.  I kept them short and many are only around 3,000 kb and are located at [http://zhkent.com](http://zhkent.com)
I know there are a couple people looking at these with dial-up.
Could you guide me through how to do this on my Ubuntu feisty system?
I have Ubuntu Studio installed.
Have been fighting this....

Thank you Kent

---

### Post by Jonathan Métillon on 2007-05-15
Kent,

I don't really have time to help you optimizing your videos. I've posted enough instructions to help you in the process of grabbing, editing and exporting them. Then you just have to play with the settings, mainly the FFmpeg settings. Just create custom Kino export scripts in */usr/share/kino/scripts/exports* and experiment with the different codecs available from your system. If you like WMV, you can try it, it's available in FFmpeg. And you can try memcoder also. Actually, any compressing tool you can pipe the DV stream to can be used in your Kino export scripts.

Good luck!

---

### Post by zhkent on 2007-05-15
Jonathan,
Wondered if encoding to dv so could save as something else was the same process that would be used to save videos to a lesser quality than dvd.
I think I have the transcode working.   It has been running for a while, had several gigs of video.
Thanks Kent

---

### Post by Jonathan Métillon on 2007-05-15
I'm sorry Kent, I really don't understand your question :confused:

---

### Post by zhkent on 2007-07-31
Jonathon,
Thank you very much for the info on how to do this.  I got it! :) I believe it is the only "how to" for .mod files in ubuntu.
Thanks again.:popcorn:

---

### Post by Jonathan Métillon on 2007-08-01
Thanx Kent! :guitar:

---

### Post by mavrommatis on 2007-09-09
Thanks for the excellent guide. 

I was able to extract the key command off your script to satisfy my needs: I wanted to convert my .MOD files to something that's more universal, and, if possible, smaller size (I don't need to edit them). For this, I used ffmpeg and encoded the files in h264/aac to produce MOV files. An additional benefit of this combination is that it works on Linux (totem, mplayer), PC and Mac (Quicktime 7). 

ffmpeg -i <inputfile>.MOD -deinterlace -vcodec h264 -b 4000k -acodec aac -ab 192k <output>.mov

This reduces the filesize in 1/2 and keeps the quality quite high. (My input quality was 8500k, but H264 has a better bitrate).

Anyway, I hope it's useful to anyone else trying to convert MOD to MOV on ubuntu linux.

P.

---

### Post by Unwiseone on 2007-10-24
I'm trying transcode the .mod files created by my father's JVC HDD camcorder over to .dv so he can edit them in Kino (or Cinerella, Diva, PiTiVi, etc) with no luck so far.

Anyone know which arguements should use when running ffmpeg?

---

### Post by Jonathan Métillon on 2007-10-24
Hi Unwiseone,

You honor your nickname =D> You could have easily extracted your answer from the script I've posted in this thread.

```
ffmpeg -i yourvideo.mod -croptop 84 -cropbottom 84 -aspect 16:9 -deinterlace -target dv yourvideo.dv
```Remove -croptop, -cropbottom and -aspect arguments if you don't want to convert your 4:3 videos to 16:9.

---

### Post by texagg01 on 2007-11-16
Jonathan

I am attempting to use your transcoder script and here's what happens when I run it.  And yes, I did change the ruby path to match where mine is.

eric@earache:~/Desktop/video$ transcode . -r
Transcoding to DV all JVC Everio MPEG-2 files in /home/eric/Desktop/video and subdirectories...
Transcoding /home/eric/Desktop/video/MOV039.mpg...
Transcoding /home/eric/Desktop/video/./MOV039.mpg...
File exists, skipped.
/bin/transcode:43:in `entries': stack level too deep (SystemStackError)
        from /bin/transcode:43:in `scan'
        from /bin/transcode:49:in `scan'
        from /bin/transcode:45:in `each'
        from /bin/transcode:45:in `scan'
        from /bin/transcode:49:in `scan'
        from /bin/transcode:45:in `each'
        from /bin/transcode:45:in `scan'
        from /bin/transcode:49:in `scan'
         ... 3998 levels...
        from /bin/transcode:49:in `scan'
        from /bin/transcode:45:in `each'
        from /bin/transcode:45:in `scan'
        from /bin/transcode:127

Any ideas as to why this is happening?  It looks like a DV folder is being created and a file is being put in there, but it doesn't open in Kino.

Any help would be greatly appreciated.

---

### Post by texagg01 on 2007-11-16
I took the "-r" off and it seemed to work.  But, when I try to open the file in Kino, it's telling me that the file is not a DV file.  It then asks me if I want to import it but it fails when I try.

---

### Post by Jonathan Métillon on 2007-11-16
texagg01,

I'm very sorry but I don't know why your DV file is broken and I can't look in that issue.

My script comes with no support, use it at your own risk, etc... ;-)

---

### Post by Palmyra on 2008-02-16
I am interested in buying JVC GZ-MG130, but if I have to go through all this trouble to edit videos, I think I will look for something else. 

I would rather not log into Windows to work with the video when Ubuntu is my primary OS.  But I'll be sure to email JVC to complain about its decision to use .MOD files (why these idiots would do such a thing, I don't know).  Everyone is complaining about these .MOD files including PC & Mac users.

---

### Post by Jonathan Métillon on 2008-02-18
Palmyra,

As I suggested in my post from December 7th, 2006, you should look into the new Sony hdd camcorders. Maybe their AVCHD format will be easier to use on Linux.

Panasonic also entered the hdd camcorders game with the SDR-H200, Hitachi with the DZ-HS300A and Canon with the HG10. I don't know what file formats they produce.

---

### Post by daka on 2008-05-02
I had this conversion instruction working fine..

ffmpeg -i <inputfile>.MOD -deinterlace -vcodec h264 -b 4000k -acodec aac -ab 192k <output>.mov


 ...until I installed Hardy Heron.. Now I get a complaint about the 'aac' format not being handled.  Any suggestions what i may need to do to accept aac files?

Daka

---

### Post by haggus on 2008-05-11
Ok so I tried all the instructions from post number 8 and I'm getting nothing

transcode . -r
transcode: option requires an argument -- r
transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
'transcode -h | more' shows a list of available command line options.
 I have tried half a dozen variants for the argument all return the above.

function mod2mpg() { find . -type f -name *.MOD -exec sh -c 'mv "{}" `dirname "{}"`/`basename "{}" | sed "s/MOD/mpg/"`; echo {}' \;;  }

added to the bottom of ~/basrc mod2mpg gives me command not found

I'm using 7.10 32bit so far I just have mod files can't convert them.

---

### Post by Dteyn on 2008-05-18
This script works for me to convert into AVI files

[http://mod2avi.sourceforge.net](http://mod2avi.sourceforge.net)

---

### Post by Jonathan Métillon on 2008-05-18
> **Dteyn said:**
> This script works for me to convert into AVI files  If you want to work with Kino, this won't be enough. Kino really only supports DV.

---

### Post by highrik on 2008-05-18
hi 

I've bought a JVC HardDrive Camcorder (GZ-MG364) and I've just become painfully aware of the whole .MOD file issue. I've recently migrated from window 2000 to ubuntu (Hardy Heron) and find ubuntu fantastic...everything is so easy and installing software is a dream :).  In window 2000 I used Media Player Classic to view my files as it was quite happy with .MOD's. and similarly totem in ubuntu.

I now want to start editing some of my video files and have been following Jonathan's guide on post 8 of this thread, with the intention of first getting kino video editor to work, and then learning how to use it (I have no prior experience of editing video).

I've run into my first problem.  Using gedit I've edited the ~/.bashrc file with the suggested code:

```

function mod2mpg() { find . -type f -name *.MOD -exec sh -c 'mv "{}" `dirname "{}"`/`basename "{}" | sed "s/MOD/mpg/"`; echo {}' \;;  }

```

But when I type in mod2mpg none of the files are changed and I get the following read out in the terminal:

```

find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression] 

```

I have no idea what the problem is so any help would be much appreciated.

Thanks, Rick

---

### Post by Jonathan Métillon on 2008-05-18
> **highrik said:**
> But when I type in mod2mpg none of the files are changed

Hi Highrik,

You should specify the path to the directory containing the videos to rename.

If you already are in this directory, just append a dot to the command so it will consider current directory:

```
mod2mpg .
```

 [COLOR=Red]**EDIT : forget that.**[/COLOR] The dot is already included in the command. I don't know what happens and it's been a very long time I've not used these tools (no time for video editing since months), and I don't have the time to investigate that right now, sorry. Maybe it's just the order of the arguments passed to the find command. Someone, please?

---

### Post by highrik on 2008-05-20
ok, not to worry :) Anyway..at the moment I'm ploughing through a huge  tutorial/document about the CLI and how to use bash commands..it's kinda taking up a lot of time so my video editing plans are temporarily on hold.

As I've been messing around with the terminal I tried what Daka tried in post 26 i.e.

```

ffmpeg -i <inputfile>.MOD -deinterlace -vcodec h264 -b 4000k -acodec aac -ab 192k <output>.mov

```

I got the same complaint..wondered if anyone has any thoughts on that?

thanks,

---

### Post by chewearn on 2008-05-20
> **highrik said:**
> ok, not to worry :) Anyway..at the moment I'm ploughing through a huge  tutorial/document about the CLI and how to use bash commands..it's kinda taking up a lot of time so my video editing plans are temporarily on hold.

As I've been messing around with the terminal I tried what Daka tried in post 26 i.e.

```

ffmpeg -i <inputfile>.MOD -deinterlace -vcodec h264 -b 4000k -acodec aac -ab 192k <output>.mov

```I got the same complaint..wondered if anyone has any thoughts on that?

thanks,


[http://ubuntuforums.org/showpost.php?p=4380982&postcount=17](http://ubuntuforums.org/showpost.php?p=4380982&postcount=17)

.

---

### Post by E-babe on 2008-05-26
Sorry for being such a noob.. but what do you guys mean when u say
"edited the ~/.bashrc file with the suggested code:"

Code:

function mod2mpg() { find . -type f -name *.MOD -exec sh -c 'mv "{}" `dirname "{}"`/`basename "{}" | sed "s/MOD/mpg/"`; echo {}' \;;  }

I have no idea how these programming stuff works. Please tell me abou tthis step..

---

### Post by Dteyn on 2008-05-26
[http://mod2avi.sourceforge.net](http://mod2avi.sourceforge.net)

Works like a charm

---

### Post by highrik on 2008-05-29
Hi E-babe

I'm a bit clueless about programming and stuff too..I'm a nurse so there's not much call for it in my line of work :)  The way I see it is that the .bashrc file holds a load of instructions for doing specific things.  In the case of 

```

function mod2mpg() { find . -type f -name *.MOD -exec sh -c 'mv "{}" `dirname "{}"`/`basename "{}" | sed "s/MOD/mpg/"`; echo {}' \;; }

```

its the instructions to convert .MOD files to .mpg files.  So when I type mod2mpg (which i can see in the above code) all my .MOD file should have been changed.....but weren't :)

I've been learning bash just lately and have covered some of the basic stuff...i've found this site really helpful [http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php).

Currently I convert my .MOD files manually via a bash terminal i.e.

```

$ mv vid_file.MOD new_vid_file.mpg

```

This works well and I have been doing basic editing with Avidemux and have also managed to put my vid files on a DVD using devede. Yay! My initially horror about the whole .MOD issue is fast fading.

Rick

---

