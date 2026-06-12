---
title: "Desktop Launcher problem"
date: 2012-12-13
forum: General Help
---

### Post by paulemony on 2012-12-13
Ubuntu 11.10

Trying to create desktop launcher for java thingy that currently lives in folder Downloads/TerraMaster_r32 and is opened with command **java -jar terramaster.jar** so in terminal this works:
```
cd Downloads/TerraMaster_r32 && java -jar terramaster.jar
```
but when this is entered as command in Create Desktop Launcher GUI this just results in **Failed to execute child process ** error message when launcher icon is clicked. Have tried ```
/home/username/Downloads/TerraMaster_r32 && java -jar terramaster.jar
```, same result. Any suggestions? Have yet to find an explanation of the differences between "Application", "Application in terminal", and "Location" options in the GUI.

---

### Post by Kirk Schnable on 2012-12-13
> **paulemony said:**
> Ubuntu 11.10

Trying to create desktop launcher for java thingy that currently lives in folder Downloads/TerraMaster_r32 and is opened with command **java -jar terramaster.jar** so in terminal this works:
```
cd Downloads/TerraMaster_r32 && java -jar terramaster.jar
```
but when this is entered as command in Create Desktop Launcher GUI this just results in **Failed to execute child process ** error message when launcher icon is clicked. Have tried ```
/home/username/Downloads/TerraMaster_r32 && java -jar terramaster.jar
```, same result. Any suggestions? Have yet to find an explanation of the differences between "Application", "Application in terminal", and "Location" options in the GUI.

How about a command with lots of direct paths... like this...

```
/usr/bin/java -jar /home/username/Downloads/TerraMaster_r32/terramaster.jar
```

Also, it would be worthwhile to try your commands in a terminal window and see if they work there.  They will likely throw much more useful error messages than "failed to execute child process".

---

### Post by paulemony on 2012-12-14
Gave up on Desktop Launcher & did a shell script instead.

---

