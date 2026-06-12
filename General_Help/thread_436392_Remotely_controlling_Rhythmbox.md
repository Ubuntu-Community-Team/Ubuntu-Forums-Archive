---
title: "Remotely controlling Rhythmbox"
date: 2007-05-07
forum: General Help
---

### Post by hupp3l on 2007-05-07
Here is my setup: I have my main pc with windows on it and then my laptop with ubuntu feisty. My laptop is connected to an amp and pretty decent sized speakers but it sits out of quick reach to skip a song.

what I need: some plugin for rhythmbox that would allow me to connect to it and skip songs, maybe through a service such as telnet. Really basic I just need to skip a song that I do not want to listen to.

what I used to do: I used to have windows on both machines, and used foobar with foobar control server which just basically allowed me to just type in play in a telnet client and my music would start playing, or next and it would skip the song. 

If you know of any such plugin or you know if it could be made, please let me know. :guitar:

---

### Post by stylishpants on 2007-05-07
No plugin is needed.  Recent Rhythmbox versions come with the rhythmbox-client command, which is designed for controlling Rhythmbox from the command line.

```
fhanson@fhanson:/usr/share/doc/mail-notification$ rhythmbox-client --help
Usage:
  rhythmbox-client [OPTION...]

Help Options:
  -?, --help                 Show help options

Application Options:
  --debug                    
  --no-start                 Don't start a new instance of Rhythmbox
  --quit                     Quit Rhythmbox
  --no-present               Don't present an existing Rhythmbox window
  --hide                     Hide the Rhythmbox window
  --next                     Jump to next song
  --previous                 Jump to previous song
  --notify                   Show notification of the playing song
  --play                     Resume playback if currently paused
  --pause                    Pause playback if currently playing
  --play-pause               Toggle play/pause mode
  --play-uri=URI to play     Play a specified URI, importing it if necessary
  --enqueue                  Add specified tracks to the play queue
  --clear-queue              Empty the play queue before adding new tracks
  --print-playing            Print the title and artist of the playing song
  --print-playing-format     Print formatted details of the song


```

---

### Post by hupp3l on 2007-05-07
I can't use that to control rhythmbox from my pc with windows though.

---

### Post by stylishpants on 2007-05-09
You can use it from windows if you first connect to your ubuntu box using telnet (or ssh.)  This is the same as your old solution, as far as I can tell from your message.

---

### Post by hupp3l on 2007-05-09
Thank you I am able to connect through ssh and everything looks like it should be working but when I use the rhythmbox-client I get this error

hupp3l@hupp3l-laptop:~$ rhythmbox-client --play

(rhythmbox-client:23390): Rhythmbox-WARNING **: Failed to execute dbus-launch to autolaunch D-Bus session

I get the same no matter if I run it as root or not.

---

### Post by dskippy on 2007-05-09
I actually made an account just so I could post the rhythmbox-client answer you gave. In the time it took me to make an account the answer was given. Nice to see the community is very alive. I do, however, think the answer is a little less that satisfactory. I came on to ask if anyone has solved the problem better. Apparently rhythmbox is a lirc client and can take lirc messages directly. The messages it can take I found at this link:

[http://gentoo-wiki.com/HOWTO_LIRC#Using_LIRC_with_rhythmbox](http://gentoo-wiki.com/HOWTO_LIRC#Using_LIRC_with_rhythmbox)

This provides more than rythmbox-client does. Particularly the ability to toggle shuffling and change the volume. Does anyone know why this is not working on unbuntu? This is an example of my .lircrc file

begin
prog = rhythmbox
button = PLAY
config = play
end

I am using a snapstream firefly RF and my PLAY button is correct I'm sure. It works with a host of other programs, just not rhythmbox. On the gentoo page I showed emerge needs to send options to build with lirc support. Is it possible that the ubuntu package doesn't have lirc support? Thanks.

---

### Post by hupp3l on 2007-05-09
I think you misread my problem. I am not using an infrared remote. I basically want to control my rhythmbox through my Local network, but thanks for trying to help.

BTW on that error that I am getting, if I type play, is it trying to send the music back to my windows pc? it should play the music on my linux machine but I think it has a problem because it is trying to play the music back on my windows pc

---

### Post by dskippy on 2007-05-09
You're right. I did. I should post to different thread. This is kind of unrelated.

---

### Post by spd106 on 2007-10-15
Sorry for resurrecting an old thread.

I've found that you can control Rhythmbox  over ssh by using screen. You must start a screen session from the music server in order for the dbus environment variables to be set correctly. It won't work if you start it from an ssh connection, I'm not sure why.

On the client, ssh into the server and re-attach to the screen session. Now you can use rhythmbox-client --play-pause etc to control Rhythmbox.

You can detach from the screen at any time and Rhythmbox will continue to play.

---

