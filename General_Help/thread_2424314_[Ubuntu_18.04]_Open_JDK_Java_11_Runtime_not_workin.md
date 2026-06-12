---
title: "[Ubuntu 18.04] Open JDK Java 11 Runtime not working"
date: 2019-08-06
forum: General Help
---

### Post by donnymurph on 2019-08-06
[COLOR=#1A1A1B][FONT=&quot]I'm trying to install [corpus linguistics software]("http://corpora.lancs.ac.uk/lancsbox/download.php") into my system.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]After downloading and extracting the .tar.xz file, I right clicked on the .jar file, then went to Properties - Permissions - Allow executing file as program.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]I used the following command to install Java:[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]$ sudo apt install openjdk-11-jdk[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]I then right clicked on the .jar file again, selected Open with Open JDK Java 11 Runtime and... Nothing happened. What can I do?[/FONT][/COLOR]

---

### Post by donnymurph on 2019-08-06
UPDATE:

I ran the following command:

[COLOR=#1A1A1B][FONT=&quot]> java -jar /home/donnymurph/Downloads/LancsBox/LancsBox.jar

And I received this error message:

[/FONT][/COLOR]> Exception in thread "main" java.lang.ExceptionInInitializerError
	at uk.ac.lancs.cass.lancsbox.LancsBox.<clinit>(LancsBox.java:70)
Caused by: java.util.MissingResourceException: Can't find bundle for base name Messages, locale es_ES
	at java.base/java.util.ResourceBundle.throwMissingResourceException(ResourceBundle.java:2055)
	at java.base/java.util.ResourceBundle.getBundleImpl(ResourceBundle.java:1689)
	at java.base/java.util.ResourceBundle.getBundleImpl(ResourceBundle.java:1593)
	at java.base/java.util.ResourceBundle.getBundleImpl(ResourceBundle.java:1556)
	at java.base/java.util.ResourceBundle.getBundle(ResourceBundle.java:857)
	at uk.ac.lancs.cass.lancsbox.gui.GUISettingsManager.<clinit>(GUISettingsManager.java:53)
	... 1 more


---

### Post by Holger_Gehrke on 2019-08-06
Try changing the working directory to the directory with the jar and the directory resources.
```
cd ~/Downloads/LancsBox
java -jar LancsBox.jar

```
Seems the program expects to find it's resources-directory in a directory named 'resources' in the current working directory.

Holger

---

### Post by donnymurph on 2019-08-06
> **Holger_Gehrke said:**
> Try changing the working directory to the directory with the jar and the directory resources.
```
cd ~/Downloads/LancsBox
java -jar LancsBox.jar

```
Seems the program expects to find it's resources-directory in a directory named 'resources' in the current working directory.

Holger

That got the program up and running. Thanks. Will I need to launch this way every time? I'd prefer to install if possible.

---

### Post by Holger_Gehrke on 2019-08-07
I'm not sure what you mean by 'install'. If you mean 'move it out of the "Download"-directory and make it possible to start it from the GUI' then here's how to do that.
Create a directory for the program somewhere inside your $HOME and move the jar-file and the resources-directory there. Create a [.desktop-file]("https://specifications.freedesktop.org/desktop-entry-spec/latest/") for the program with an "Exec"-line of 'Exec=java -jar /home/donnymurph/DIRECTORY/LancsBox.jar' and a "Path"-line of 'Path=/home/donnymurph/DIRECTORY/LancsBox.jar' (replace 'DIRECTORY' with the name of your directory for the program). Depending on your Desktop Environment creating a .desktop-file might be as simple as right-clicking on the Desktop and selecting "Create Starter" from the context-menu and filling out a form or you might have to write it yourself in an editor. If the linked description of .desktop-files seems too theoretical to you, take a look at the existing .desktop-files in /usr/share/applications/. Move the new .desktop-file to ~/.local/share/applications/ (create that  directory if it doesn't exist yet). Done.

Holger

---

### Post by dragonfly41 on 2019-08-07
> **donnymurph said:**
> [COLOR=#1A1A1B][FONT=&amp]I'm trying to install [corpus linguistics software]("http://corpora.lancs.ac.uk/lancsbox/download.php") into my system.[/FONT][/COLOR]


You might also be interested in this [suite of tools]("https://www.laurenceanthony.net/software.html").

I installed toolset into /opt/Ant_Tools/ and launch from desktop menu.

---

