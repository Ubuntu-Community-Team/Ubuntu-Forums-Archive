---
title: "amsn plugin atuo load."
date: 2008-01-20
forum: General Help
---

### Post by b.eser on 2008-01-20
Guys i need help. I load the plugin inkdraw on amsn. It is working nice when i load it. But whenever i open amsn i need to load that plugin again again. Now i installed the music plugin and it is the same. Whenever i open amsn i need to load it again. Isnt there a way to make is load automaticly and remember the configuration i have done for that plugin ? I am sick of doing it everytime i open amsn.

---

### Post by gsiliceo on 2008-01-20
I suggest upgrading your amsn version.
Wich one you have?

---

### Post by b.eser on 2008-01-20
i just installed the last version. But it is still the same. And i figured out something. If i click to remember my account it creates a folder under /home/user/.amsn/ with the name of my profile. And it keeps the preferences. It creates a plugins.xml file there and when i become online on that profile. It remembers my choices. But i dont want it to remember my profile. Any way to create a xml file or something for general ? I mean then all the profiles can have those plugins loaded when they become online.

---

### Post by gsiliceo on 2008-01-20
Delete the .amsn folder and the next time you open aMsn go to the menu account and the to advanced, scroll down all the way and tick disable profiles.
I think those are the names my amsn is in spanish :)

---

### Post by b.eser on 2008-01-22
i solved the problem by mailing to the developers of amsn. I am posting the reply sent to me

"

By the way, if you just want to make it work, edit the file
'plugins.tcl', and find the lines:


                # check if this is the default profile
                if { $HOME == $HOME2 } {
                        plugins_log core "save_config: Default
profile, no plugin configuration saved!\n"
                        catch {file delete -force [file join ${HOME}
plugins.xml]}
                        return 0
                }

comment them out like:

                # check if this is the default profile
                #if { $HOME == $HOME2 } {
                #        plugins_log core "save_config: Default
profile, no plugin configuration saved!\n"
                #        catch {file delete -force [file join ${HOME}
plugins.xml]}
                #        return 0
                #}

or just delete them, and you should get the desired behavior.

Greets.
"

By the way plugins.tcl file is in the directory which amsn is installed. It is /usr/share/amsn in my pc. Probably the same on everywhere :)

---

