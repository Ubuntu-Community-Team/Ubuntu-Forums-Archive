---
title: "Script is not working right only if started from .bashrc"
date: 2007-12-15
forum: General Help
---

### Post by alpharesearch on 2007-12-15
Hello,

I have this menu.sh script as a help to call some commands I need to start all the time... if I start it in the bash it works all like expected... but if I put it on the end of .bashrc like ./menu.sh weird stuff starts happen, first mc takes 10 seconds instead of <1 second to start, second the svn diff writes (like key press d) once? After I exit the script with q mc still needs 10 seconds to start. 
If i take it out of .bashrc  and just type ./menu.sh it works fine? It is the same under console and x...

This is my first shell script modification , I used a skeleton from a tutorial. 
 
Any idea what I did wrong?

here is my menu.sh script:
```

#!/bin/bash
function anykey
{
    echo ""
    echo ""
    echo -n "press any key to continue..."
    read -n1
}

selection=
until [ "$selection" = "q" ]; do
clear
printf "\033[1;37;44m"
echo "&#9484;&#9472;&#9472;&#9472;&#9516;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;"
printf "&#9474;   &#9474;\033[0;30;46mBlender Development Start Menu V1\033[1;37;44m&#9474;\n"
echo "&#9500;&#9472;&#9472;&#9472;&#9532;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;"
echo "&#9474; 1 &#9474;mc in blender dev directory      &#9474;"
echo "&#9474; 2 &#9474;compile blender with scons       &#9474;"
echo "&#9474; 3 &#9474;cscope in /source/blender/src/   &#9474;"
echo "&#9474; 4 &#9474;svn update non dev, scons, run   &#9474;"
echo "&#9474; 5 &#9474;start non dev blender            &#9474;"
echo "&#9474; 6 &#9474;start blender under gdb on :0    &#9474;"
echo "&#9474; 7 &#9474;start blender under gdb on :1    &#9474;"
echo "&#9474; 8 &#9474;start blender under gdb on :2    &#9474;"
echo "&#9474; 9 &#9474;start x :1 if auth is granted    &#9474;"
echo "&#9474; 0 &#9474;start x :2 if auth is granted    &#9474;"
echo "&#9474; d &#9474;create new diff file in home     &#9474;"
echo "&#9474; q &#9474;quit this menu and return to bash&#9474;"
echo "&#9500;&#9472;&#9472;&#9472;&#9532;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;"
printf "&#9474;   &#9474;\033[0;30;46menter selection:                 \033[1;37;44m&#9474;\n"
echo "&#9492;&#9472;&#9472;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;"
printf "\033[17;23H" 
printf "\033[0;37;49m" 

    read -n1 selection
    echo " "
    case $selection in
        1 ) cd ~/bf-blender-dev/blender/; mc;;
        2 ) clear; cd ~/bf-blender-dev/blender/; scons; anykey;;
	3 ) clear; cd ~/bf-blender-dev/blender/source/blender/src/; export EDITOR=mcedit; cscope ; anykey;;
	4 ) clear; cd ~/bf-blender-org/blender; svn update; scons; cd ~/bf-blender-org/install/linux2; ./blender ; anykey;;
	5 ) clear; cd ~/bf-blender-org/install/linux2; ./blender ; anykey;;
	6 ) clear; cd ~/bf-blender-dev/install/linux2; export DISPLAY=:0;gdb ./blender ; anykey;;
	7 ) clear; cd ~/bf-blender-dev/install/linux2; export DISPLAY=:1;gdb ./blender ; anykey;;
	8 ) clear; cd ~/bf-blender-dev/install/linux2; export DISPLAY=:2;gdb ./blender ; anykey;;
        9 ) clear; startx -- :1; anykey;;
        0 ) clear; startx -- :2; anykey;;
	d)  clear; cd ~/bf-blender-dev/blender/; (svn diff > ~/bf-diff_patch/blender_patch$(date +%F+%T).diff) ; anykey;;
        q ) clear ; exit ;;
        * ) 
    esac
done
exit 0

```

---

