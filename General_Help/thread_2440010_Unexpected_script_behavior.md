---
title: "Unexpected script behavior"
date: 2020-04-04
forum: General Help
---

### Post by Quaxo76 on 2020-04-04
Hello,
I tried writing a simple script that converts any .flac files present in its own folder, into .mp3 files, and if successful, deletes the original .flac file.
If I run the script by just running ```
 ./ScriptName.sh
``` it works; 
but it I run it as superuser ```
sudo ./ScriptName.sh
``` or if I run it like this: ```
sh ./ScriptName.sh
```
something unexpected happens:
- the echo command does not parse the -e option (i.e. it actually prints -e on screen)
- much worse: when the ffmpeg command is called, it returns no error, so the script proceeds to delete the flac file; but only AFTER this, ffmpeg actually tries to convert the file, obviously failing because it doesn't exist any more. So I loose the flac without having the mp3. Shouldn't it return no error only if the file has actually been converted?

I'm a total beginner at script programming, so I have no idea what's going on. Can anyone help me? This is the script:

```

echo There are "`ls -1 *.flac | wc -l`" flac files.
echo There are "`ls -1 *.mp3 | wc -l`" mp3 files.

RED='\033[0;31m' # Red
CYAN='\033[0;36m' #Cyan
YELLOW='\033[1;33m' #Yellow
BLUE='\033[0;34m'
NC='\033[0m' # Neutral color

for x in *.flac
do
OrigFile="$x"
DestFile="`basename "$x" .flac`.mp3"
echo -e "${NC}OrigFile = ${CYAN}$OrigFile${NC}"
if [ -e "`basename "$x" .flac`.mp3" ]
then
  echo -e "${YELLOW}$DestFile already exixts, deleting flac...${NC}"
  if rm -f "$x" ; then
    echo Deleted.
  else
    echo -e "${RED}Error while deleting $OrigFile.${NC}"
  fi
else
  echo -e "${BLUE}$DestFile${NC} does not exist. Creating..."
  if ffmpeg -i "$x" -q:a 0 -map_metadata 0 -id3v2_version 3 "`basename "$x" .flac`.mp3" &> /dev/null ;
  then
    echo -e "${BLUE}$FileDestinazione${NC} successfully created."
    echo Deleting .flac file ...
    if rm -f "$x" ; then
      echo Deleted.
    else
      echo -e "${RED}Error while deleting $OrigFile.${NC}"
    fi
  else
    echo -e "${RED}Error while creating $DestFile.${NC}"
  fi
fi
done

```

---

### Post by lvm on 2020-04-04
echo is a built-in shell command and works differently in different shells: bash supports -e option, sh (or rather dash which is installed in ubuntu) doesn't. You may want to specify that this script is to be run in bash by adding #!/bin/bash as the first line of the script.

---

### Post by Quaxo76 on 2020-04-05
Thank you very much! Is this the reason why also the ffmpeg command fails?

Cristian

---

### Post by lvm on 2020-04-05
It doesn't fail. &> is bash-specific, dash treats &> as plain & (asynchronous execution), then redirection and that's what it does - starts ffmpeg asynchronously. It's better to use >& as all shells support it.

---

