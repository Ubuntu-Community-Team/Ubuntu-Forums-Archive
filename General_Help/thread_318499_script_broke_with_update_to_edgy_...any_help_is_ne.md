---
title: "script broke with update to edgy ...any help is needed"
date: 2006-12-14
forum: General Help
---

### Post by sefs on 2006-12-14
The script below broke when I updated to edgy. can anyone help?

```

#!/bin/sh
# /mnt/hd2/data/tc/lhd3.sh

DoMnt()
{
	COUNTER=0
	TCSTATUS="truecrypt: Incorrect password"
	DIALOGTEXT="Enter your password."
	GETPASSWD=""
	while [[ $COUNTER < 3 ]] && [[ $TCSTATUS == "truecrypt: Incorrect password"* ]] ; do
		GETPASSWD=`zenity --title "Password" --entry --hide-text --text "$DIALOGTEXT"`
		if [[ ${#GETPASSWD} != 0 ]] ; then
			TCSTATUS=$(/usr/bin/truecrypt /mnt/hd2/datadrive/datadrive /mnt/hd3 -p$GETPASSWD --password-tries 1 2>&1)
			if [[ ${#TCSTATUS} != 0 ]] ; then
				zenity --title "Status" --info --text "$TCSTATUS"
			fi
			let COUNTER=COUNTER+1 
		else
			let COUNTER=3 
		fi
	done
	return 0
}

DoMnt

```

it launches a dialog but now the dialog does not appear.
When i run from terminal i get...

```

lhd3.sh: 25: cannot open 3: No such file
lhd3.sh: 25: [[: not found

```

---

