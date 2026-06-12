---
title: "whiptail file menu help"
date: 2013-02-26
forum: General Help
---

### Post by mecj5 on 2013-02-26
[COLOR=black][FONT=Tahoma]I have googled, searched the forums, and good old trial and error and so far have not been able to solve why this doesn’t work i am trying to make a file select menu with whiptail that feeds the selected file into the next command please help me[/FONT][/COLOR]
```

4)
dir=$(whiptail --title "Extract and merge ac3 only" --inputbox "What is the directory of your files (full path pls)?" 8 78 3>&1 1>&2 2>&3)
i=0
s=65 #decimal ASCII "A"
cd "$dir" && for f in *
do
#convert to octal then ASCII characters for select tag
files[i]=$(echo)
files[i+1]="$f" #save file name
((i+=2))
((s++))
done
choices=$(whiptail --title "Extract and merge ac3 only" --scrolltext --menu "Make a choice" 16 78 8 "${files[@]}" 3>&1 1>&2 2>&3)
input=$(echo "$choices" | sed 's/.vob //g' 3>&1 1>&2 2>&3)
map=$(whiptail --title "Extract and merge ac3 only" --inputbox "What is the map number of the the audio?" 8 78 3>&1 1>&2 2>&3)
whiptail --title "Extract and merge ac3 only" --yesno "Your file is '$input.vob' and your audio map number is '$map', is that correct?" 8 78
exitstatus=$?
if [ $exitstatus = 0 ]; then
cd "$dir" && ffmpeg -i "$input.vob" -map "$map" -c:a copy "$input.ac3" && ffmpeg -i "$input.vob" -i "$input.ac3" -map 0:0 -map 1:0 -c:v copy -c:a copy "$input AC3 Only.vob" && rm "$input.ac3"
fi
;;

```

---

