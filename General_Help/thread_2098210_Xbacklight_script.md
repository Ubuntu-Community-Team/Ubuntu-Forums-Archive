---
title: "Xbacklight script"
date: 2012-12-26
forum: General Help
---

### Post by D4rkH4nd on 2012-12-26
[SIZE=2]After i fist installed Ubuntu i noticed that my backlight was really dim. So i stumbled [SIZE=2]on Xbacklight. I like it[SIZE=2], its simple and does the job. BUT i hate to have to [SIZE=2]open terminal and change it when i login , playing diff games, reading , web[SIZE=2]. SO i made this simple bash script. 

Its very simple and works well. Hope this helps at least someone.

[SIZE=2][~~~~>Link to script <~~~]("http://pastie.org/private/eshhwcsxze9fprcytvmq")

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
```
#!/bin/bash

backlight="bash xbacklight.sh"

function title {
  echo "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
  echo "~          D4rkH4nd's          ~"
  echo "~      xbackligh Script        ~"
  echo "~   A BloodyNose Production    ~"
  echo "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
}

function check {
  if dpkg -s xbacklight > /dev/null 2>&1 ;
    then
      echo "Xbacklight installed"
    else echo "Xbacklight not installed"
    read -p "Would you like to install Xbacklight ?[y]es or [n]o :" install
    
    case $install in
    
    y|Y)        echo "Installing xbacklight, enter sudo password when promped"
              sudo apt-get install xbacklight
              $backlight
      ;;
              
    n|N)         echo "Why use this script if you dont want xbacklight ???"
              exit
      ;;
      
    *)        echo "Thats not a option. Try again."
             check
      ;;
      esac
  fi
}

function menu {
  if dpkg -s xbacklight > /dev/null 2>&1 ;
    then
    read -p "Set your screens brightness: Any number between 1 & 100: " level
    
    case $level in
    
    exit|EXIT)        echo "Closing ... bye"
              sleep 3
              clear
    ;;
    
    $level)        if [[ $level =~ ^[0-9]+$ ]]
                then 
                  xbacklight -set $level
                  clear
                  echo "Brightness changed to" $level"%"
                  menu
              else echo "not a number"
                   sleep 1
                   clear
                   menu
              fi
    ;;
    
    esac
    else echo "Error Xbacklight Not Installed. Restart script and install"
     clear
     check
  fi
}

title
sleep 3
check
sleep 2
menu
```

---

