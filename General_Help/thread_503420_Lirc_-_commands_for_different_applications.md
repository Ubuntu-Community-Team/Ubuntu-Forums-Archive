---
title: "Lirc - commands for different applications"
date: 2007-07-17
forum: General Help
---

### Post by extension on 2007-07-17
The problem I am having is that I cant access certain functions with my remote through MythTV like fast forwarding/rewinding songs, changing the volume and searching for a song. Maybe I misunderstand how lirc works but I currently believe all I have to do is add some commands to my lircrc the only problem being I dont know what commands are available for the applications I need to control. Is there a central location to find these commands and is this the right approach?

Is adding something like:

begin
prog = xine
button = Vol+
repeat = 3
config = VolumeUp
end

the solution I am looking for?

---

