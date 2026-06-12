---
title: "Create new profile thunderbird automatically with python"
date: 2008-04-04
forum: General Help
---

### Post by nahydy on 2008-04-04
HI every one,
I want to know how can i create automatically a new profile in thunberbird and do all customization such the Email address or logname using a python script. I would like take all information about the user from another script which allows me to create a new user in my system and enter relative information.This is the script below: 
```

def add():
        login=raw_input('Enter logname: ')
	res=os.system('getent group|grep '+login)
	if (res == 256):
                os.system('useradd -m -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,lpadmin,scanner,admin -s /bin/bash '+login)
		pwd=os.system('passwd '+login)	
                printer(login+' added',0)
	else:
                printer(login+' exist',0)

```
When i looked in the internet i found that i can manage user using this line of command:
```
./thunderbird -ProfileManager 
```
But it opens to me a window and where i can create the new profile. Any one can help me.

---

### Post by justleen on 2008-04-04
[there are more commandline options]("http://developer.mozilla.org/en/docs/Command_Line_Options#User_Profile"), which allow to create specific profiles.
Links is for mozilla, but im pretty sure they work the same  for firefox/thunderbird
```

firefox -CreateProfile "JoelUser c:\internet\moz-profile"

```


Try man thunderbird for info in thunderbird options.

---

