---
title: "Howto: Setup more realistic text-to-speech voices WITHOUT Festival."
date: 2015-03-30
forum: General Help
---

### Post by Slackwarejohn on 2015-03-30
To thank Ubuntu Forum for its (closed) post, "[Howto: Setup more realistic voices in Festival]("http://ubuntuforums.org/showthread.php?t=677277&page=2&")," I've registered and included this new how-to. Best wishes!

It's 2015, and if you simply want a nice, compact text-to-speech program in Linux with a good voice, then forget Festival. flite+hts_engine is the way to go.

Moreover, you don't have to install anything system-wide. You can compile everything in a folder in your home directory and just call it from there.

However, there are some tricks involved. I've included a shell script below that tells time, so you can see how it all works together. But to start, get the programs and the good voice and compile them as follows:
```
mkdir ~/hts
cd ~/hts
```

Tricky: you'll need to create a FIFO file with a .wav extension for all this to work.
Create your FIFO .wav file and call it something. I've called it FIFO.wav here.
```
mkfifo ~/hts/FIFO.wav
```

Now get the software.
You need hts_engine_API, Flite+hts_engine, and HTS voice
These are the current versions as of March 2015.
NOTE: these version names may change with new developer activity, and so you may need to download newer versions than the ones given here.
And be sure to reflect any version name changes in EVERYTHING below.
You should be able to find and download the latest versions at [http://hts-engine.sourceforge.net/](http://hts-engine.sourceforge.net/)
```
wget -c http://downloads.sourceforge.net/hts-engine/hts_engine_API-1.09.tar.gz
wget -c http://downloads.sourceforge.net/hts-engine/flite%2Bhts_engine-1.06.tar.gz
wget -c http://downloads.sourceforge.net/hts-engine/hts_voice_cmu_us_arctic_slt-1.05.tar.gz

```
unpack everything
```
for i in *.gz
do
tar xzf "$i"
done

```
compile hts_engine_API-1.09
```
cd ~/hts/hts_engine_API-1.09/
./configure
make

```
compile flite+hts_engine
NOTE: this relies on your having compiled hts_engine_API-1.09 in the directory ~/hts/hts_engine_API-1.09/, as above.
```
cd ~/hts/flite+hts_engine-1.06/

./configure \
     --with-hts-engine-header-path="$HOME"/hts/hts_engine_API-1.09/include \
     --with-hts-engine-library-path="$HOME"/hts/hts_engine_API-1.09/lib
make

```
You're done! (The actual voice just needed to be extracted, not compiled; so it's already in its directory, waiting for you).

Two problems:

a) flite+hts_engine only outputs to a .wav file. Therefore, the key refinement is to create a FIFO file with a .wav suffix, and tell flite+hts_engine to output to that. Then aplay can play that FIFO .wav file, and you will hear the text on the fly as it is interpreted by the engine.

b) flite+hts_engine only reads text files (not words on the command line), and it only reads the FIRST line of a text file. So, to speak a multi-line text, we must do that line-by-line.

To see how this all works, a sample shell program is below. NOTE: this shell program relies on the locations of files as you compiled above.

Name the script something like "TellTime.sh" and save it where you wish, such as ~/TellTime.sh. Then make it executable:
```
chmod 755  ~/TellTime.sh
```
Then you can hear the time by calling:
```
~/TellTime.sh
```

###### The example shell program begins below. Remember that all the files that are called rely on your compiling at the locations as above. The first line of the program should be: "#! /bin/sh" (without the quotes)

```
#! /bin/sh

# Get the time
ttime=$( date +%l:%M%p | sed -e s,"A"," A.", -e s,"P"," P.", )

# Put it in '~/time.txt'
echo "The time is $ttime." > ~/time.txt
# repeat the time on a new line (so we get a multi-line text to play with)
echo "$ttime." >> ~/time.txt

# NOTE: flite+hts_engine only reads the FIRST line of a text file.
# So, to speak a multi-line text, we must read that text file
#   one line at a time into another file ( such as ~/line.txt),
#   and then repeatedly call flite+hts_engine
#   to read (each new line) in ~/line.txt

# First, always flush the FIFO buffer
dd if=~/hts/FIFO.wav iflag=nonblock of=/dev/null >> /dev/null 2<&1

# Set up a loop to read ~/time.txt line-by-line
#   put each line into ~/line.txt
#   and have flite_hts_engine read (each new line) in  ~/line.txt

cat ~/time.txt |
while read line
do
    echo "$line" > ~/line.txt

    # Set up aplay to play when FIFO.wav gets some sound
    # DON'T forget the '&' at the end of the line!

    cat ~/hts/FIFO.wav | aplay -q &

    #   Here are relevant flite_hts_engine options explained:
    #   -m  : the location of the voice; you must have this option
    #   -s  : the sound sample rate in Hz (48000 should work; or 44100)
    #   -r  : speech speed rate (0.5=half speed, 1.0 is default, 2.0=twice speed)
    #   -fm : raise the pitch with "1", "2.3", or lower it with "-1" "-2", etc.
    #       (for fun, try way high: -fm "12", and way low: -fm "-24")
    #   -o  : the output; this must be a .wav filename
    #   the input must be a text file

    # And this is how you call flite_hts_engine (reading ~/line.txt):

    ~/hts/flite+hts_engine-1.06/bin/flite_hts_engine \
    -m ~/hts/hts_voice_cmu_us_arctic_slt-1.05/cmu_us_arctic_slt.htsvoice \
    -s 48000 \
    -r 0.7 \
    -fm "-1.3" \
    -o ~/hts/FIFO.wav \
    ~/line.txt

    # IMPORTANT: call 'wait' to make sure that both aplay and flite_hts_engine are completely done before continuing

    wait
done

###### End shell program

```

UPDATE:
On a lark, I changed the sound sample rate from 48000 (which is what the metadata in cmu_us_arctic_slt.htsvoice says is accurate) to 44100, and obtained an even more realistic-sounding voice. Here's the settings I now use to call flite_hts_engine :
```
 ~/hts/flite+hts_engine-1.06/bin/flite_hts_engine \
    -m ~/hts/hts_voice_cmu_us_arctic_slt-1.05/cmu_us_arctic_slt.htsvoice \
    -s 44100 \
    -r 0.8 \
    -fm "2.3" \
    -o ~/hts/FIFO.wav \
    ~/line.txt

```

---

### Post by bgvozdev on 2016-03-23
Hey Slackwarejohn, thanks for sharing! I struggled a few days to make HTS voices talk on festival, but your solution is much easier.

Does anybody have an idea of how to generate these ".htsvoice" files, e.g. from the ones below? Thanks in advance.

wget -c [http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_awb_arctic-0.90-release.tar.bz2](http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_awb_arctic-0.90-release.tar.bz2)
wget -c [http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_bdl_arctic-0.95-release.tar.bz2](http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_bdl_arctic-0.95-release.tar.bz2)
wget -c [http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_clb_arctic-0.95-release.tar.bz2](http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_clb_arctic-0.95-release.tar.bz2)
wget -c [http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_jmk_arctic-0.95-release.tar.bz2](http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_jmk_arctic-0.95-release.tar.bz2)
wget -c [http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_rms_arctic-0.95-release.tar.bz2](http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_rms_arctic-0.95-release.tar.bz2)
wget -c [http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_slt_arctic-0.95-release.tar.bz2](http://www.speech.cs.cmu.edu/cmu_arctic/packed/cmu_us_slt_arctic-0.95-release.tar.bz2)

---

