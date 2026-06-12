---
title: "Conky + Audcaious Cover Art"
date: 2013-09-11
forum: General Help
---

### Post by adec2 on 2013-09-11
Hi, I have got conky running with audacious well. It shows the track information, bitrate etc but will not display any cover art. Could anyone help me?
This is my audacious template (forget the references to banshee it works)

${color light blue}                                                                         Artist - ${#FFFFFF}[--datatype=AR --maxlength=100]
${color light blue}                                                                         Album - ${#FFFFFF}[--datatype=AL --maxlength=100]
${color light blue}                                                                         Track - ${#FFFFFF}[--datatype=TN] - [--datatype=TI --maxlength=100]
${color light blue}                                                                         Time - ${#FFFFFF}[--datatype=PT] ${color light blue}${color light blue} Volume ${#FFFFFF}[--datatype=VO] ${color light blue}BitRate ${#FFFFFF}[--datatype=BR]
${image [--datatype=CA] -p 20,650 -s 215x208}${image ~/images/banshee1.png -p -280,-48 -s 1300x800}${image ~/images/bansheeiphone.png -p -135,365 -s 500x667}


I have invoked the script within the conkyrc by

${if_running audacious}
${execp ~/conkyAudacious.py --template=~/conkyAudacious.template}
$endif

Like I said it runs fine except the cover art

 i also have a audacious python script that executes when i play music in audacious. I dont want to paste the contents as it is too big. Could anyone help me please? :)

---

