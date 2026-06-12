---
title: "Bash Script Improvement"
date: 2013-12-29
forum: General Help
---

### Post by Tristan_Williams on 2013-12-29
I love to automate things.
I have mad a script which makes a menu for me to select various "apt-get" options, and allows me to input during the script.

I would love it if you guys could help me improve it.

Improvements could include:
New options
Changes to the commands used, or the format of the code.
Changes to the arrangement of options
etc...

PLEASE COMMENT YOUR CODE

NOTE:
I have added an entry to /etc/bash.bashrc:
        alias app='source /etc/app.sh'
Also, I have save the script as /etc/app.sh

Here's the origional script:
The most recent one is directly below this one.
```

#!/bin/bash

#    WARNING!!!
#    
#    This script has not been tested! Use this at your own risk!


#            HOW TO SET UP THIS SCRIPT                  
#    1. As root, open /etc/bash.bashrc                      
#                                          
#    2. Add the following line at the bottom of the file:              
#        alias app='source /etc/app.sh'                      
#    Save and exit                                  
#                                          
#    3. Now, save this script as /etc/app.sh and make it executable          
#                                          
#    4. You must restart your current terminal, or exit and start          
#          a new terminal in order for this to take effect.              
#                                          


clear    # Give a clean startup menu

# Initial List of choices
echo "1. Maintenance"
echo "2. Install Software"
echo "3. Remove Software"
echo "4. Add PPA"
echo "5. Remove PPA"
echo "6. Exit"

# Read user input to determine which action to take
read -p "Selection: " > export choice
    
    # Actions for choice 1
    if [ "$choice" == "1" ]; then
        clear
        # Maintenance sequence (upgrade twice because in some
        # cases, new dependencies need to be upgraded)
        sudo apt-get update
        sudo apt-get upgrade
        sudo apt-get install -f
        sudo apt-get upgrade
        sudo apt-get autoclean
        sudo apt-get autoremove
        echo "Maintenance Complete "
        read -p "Press any key to continue..."
        source /etc/app.sh

    # Actions for choice 2
    elif [ "$choice" == "2" ]; then
        clear
        read -p "Package to install: " > export pkg_i
        clear
        read -p "Install additional recommended packages? [y/n] " > export pkg_i_arp
            if [ "$pkg_i_arp" == "y" ]; then
                clear
                sudo apt-get install $pkg_i
            elif [ "$pkg_i_arp" == "n" ]; then
                clear
                sudo apt-get install --no-install-recommends $pkg_i
            fi
        read -p "Press any key to continue..."
        source /etc/app.sh
            
    # Actions for choice 3
    elif [ "$choice" == "3" ]; then
        clear
        read -p "Package to remove " > export pkg_r
        read -p "Remove configuration files?(recommended) [y/n] " > export pkg_r_conf
            if [ "$pkg_r_conf" == "y" ]; then
                sudo apt-get purge $pkg_r
            elif [ "$pkg_r_conf" == "n" ]; then
                sudo apt-get remove $pkg_r
            fi
        read -p "Press any key to continue..."
        source /etc/app.sh
        
    # Actions for choice 4
    elif [ "$choice" == "4" ]; then
        clear
        read -p "PPA to add (must be in form: ppa:<ppa name>/<subdirectory>)" > export ppa_add
        sudo add-apt-repository $ppa_add
        read -p "Press any key to continue..."
        source /etc/app.sh
        
    # Actions for choice 5
    elif [ "$choice" == "5" ]; then
        clear
        read -p "PPA to remove (must be in form: ppa:<ppa name>/<subdirectory>)" > export ppa_rem
        sudo add-apt-repository --remove $ppa_rem
        read -p "Press any key to continue..."
        source /etc/app.sh
        
    # Actions for choice 6
    elif [ "$choice" == "6" ]; then
        clear
        bash
    
    fi
    
# Developed by:
#
# Tristan Williams    tristan401_2000@live.com
# 

```

The initial menu looks like this:
```

1. Maintenance
2. Install Software
3. Remove Software
4. Add PPA
5. Remove PPA
6. Exit
Selection: 

```

If you provide an improvement, please provide your name and email (so I can give you credit) , and a description of what you did to improve it.

Thanks in advance :)







Edit:

This is the edited script SO FAR ( I will update it HERE as it get edited):
```

#!/bin/bash

#            HOW TO SET UP THIS SCRIPT                  
#    1. As root, open /etc/bash.bashrc                      
#                                          
#    2. Add the following line at the bottom of the file:              
#        alias app='source /etc/app.sh'                      
#    Save and exit                                  
#                                          
#    3. Now, save this script as /etc/app.sh and make it executable          
#                                          
#    4. You must restart your current terminal, or exit and start          
#          a new terminal in order for this to take effect.             

clear    # Give a clean startup menu

# Initial List of choices
echo "1. maintenance"
echo "2. install software"
echo "3. remove software"
echo "4. Search for a package"
echo "5. add ppa"
echo "6. remove ppa"
echo "7. generate package list"
echo "8. install from wget or dpkg"
echo "9. Backup important files"
echo "10. exit"

# Read user input to determine which action to take
read -p "Selection: " choice
    
    # 1. Maintenance
    if [ "$choice" == "1" ] || [ "$choice" == "maintenance" ] || [ "$choice" == "maintain" ]; then
        clear
        # Maintenance sequence (upgrade twice because in some
        # cases, new dependencies need to be upgraded)
        read -p "Check for broken PPA's? [y/n] " broken_ppa_clean
            # If yes, check for broken PPA(s)
            if [ "$broken_ppa_clean" == "y" ]; then
                clear
                echo "Checking for broken PPAs... "
                sudo apt-get update > update_app.txt
                clear
                cat update_app.txt | grep Err | cut -c 12- > broken_app.txt 

                IFS=$'\n' read -d '' -r -a lines < broken_app.txt
                 
                 # List broken PPA(s)
                echo "Found the following broken ppa's"
                echo "${lines[@]}"
                echo ""
                echo "If there are no PPAs listed above, reply 'n'"
                echo "to the prompt below"
                echo ""
                echo "It may be that the repositories are down and will be up later"
                echo "If you continue these will be deleted from your system"

                read -p "Remove files? [y/n] " cont_1
                    # If yes, remove broken PPA(s) from system
                    if [ "$cont_1" == "y" ]; then
                        clear
                        cat update_app.txt | grep Err | cut -c 12- | cut -d ' ' -f 1 > broken_app.txt 
                        IFS=$'\n' read -d '' -r -a lines < broken_app.txt
                        i="0"

                        while [[ "${lines[$i]}" != "" ]]; do
                                 grep -H "${lines[$i]}" /etc/apt/sources.list.d/*.list | cut -d ':' -f 1  > delete_app.txt
                                IFS=$'\n' read -d '' -r -a linesd < delete_app.txt
                                a="0"
                        
                            while [[ "${linesd[$a]}" != "" ]]; do

                            file="${linesd[$a]}"
                            if [ -f "$file" ]; then
                                clear
                                    echo "$file will be removed."
                                read -p "Continue with removal? [y/n] " cont_2
                                # If yes, remove $file
                                if [ "$cont" == "y" ]; then
                                    clear
                                      echo "Removing $file";
                                      sudo rm "$file"
                                    sleep 5
                                else
                                      echo "Will keep $file";
                                    sleep 5
                                fi
                            else
                                clear
                                    echo "$file not found."
                                sleep 5
                            fi

                                echo "${linesd[$a]}"
                            a=$[$a+1]
                                done
               
                        i=$[$i+1]
                        done
                    elif [ "$cont_1" == "n" ]; then
                        clear
                          echo ""
                    fi
                clear
                rm update_app.txt
                rm broken_app.txt
                rm delete_app.txt
            # If no, continue with maintenance sequence
            elif [ "$broken_ppa_clean" == "n" ]; then
                clear
                echo ""
            fi
        # Maintenance sequence
        sudo apt-get update
        sudo apt-get upgrade
        sudo apt-get install -f
        sudo apt-get upgrade
        sudo apt-get autoclean
        sudo apt-get autoremove
        echo "Maintenance Complete "
        read -p "Press any key to continue..."
        
        # Remove no-longer-needed variables
        unset choice
        unset broken_ppa_clean
        unset file
        unset IFS
        unset cont_1
        unset cont_2
        
        # Loop back to main menu
        source /etc/app.sh

    # 2. Install Software
    elif [ "$choice" == "2" ] || [ "$choice" == "install software" ] || [ "$choice" == "install" ]; then
        clear
        # Name of package to install
        read -p "Package to install: " pkg_i
        clear
        # Decide whether or not to install recommended packages/dependencies
        read -p "Install additional recommended packages? [y/n] " pkg_i_arp
            # If yes, install $pkg_i + additional recommended packages
            if [ "$pkg_i_arp" == "y" ] || [ "$pkg_i_arp" == "yes" ]; then
                clear
                sudo apt-get install $pkg_i
            # If no, install $pkg_i ONLY
            elif [ "$pkg_i_arp" == "n" ] || [ "$pkg_i_arp" == "no" ]; then
                clear
                sudo apt-get install --no-install-recommends $pkg_i
            fi
        read -p "Press any key to continue..."
        
        # Remove no-longer-needed variables
        unset choice
        unset pkg_i
        unset pkg_i_arp
        
        # Loop back to main menu
        source /etc/app.sh
            
    # 3. Remove Software
    elif [ "$choice" == "3" ] || [ "$choice" == "remove software" ] || [ "$choice" == "remove" ] || [ "$choice" == "purge" ]; then
        clear
        # Specify which package to remove
        read -p "Package to remove " pkg_r
        # Decide whether or not to remove all files related to the package
        read -p "Remove configuration files?(recommended) [y/n] " pkg_r_conf
            # If yes, remove $pkg_r and all related files
            if [ "$pkg_r_conf" == "y" ] || [ "$pkg_r_conf" == "yes" ]; then
                sudo apt-get purge $pkg_r
            # If no, remove $pkg_r ONLY
            elif [ "$pkg_r_conf" == "n" ] || [ "$pkg_r_conf" == "no" ]; then
                sudo apt-get remove $pkg_r
            fi
        read -p "Press any key to continue..."
        
        # Remove no-longer-needed variables
        unset choice
        unset pkg_r
        unset pkg_r_cong
        
        # Loop back to main menu
        source /etc/app.sh
        
    # 4. Search for a Package
    elif [ "$choice" == "4" ] || [ "$choice" == "search" ]; then
        clear
        # Specify package to search for
        read -p "Search for: " app_search
        sudo apt-cache search --names-only $app_search
        read -p "Press any key to continue..."
        
        # Remove no-longer-needed variables
        unset choice
        unset app_search
        
        # Loop back to main menu
        source /etc/app.sh
        
    # 5. Add PPA
    elif [ "$choice" == "5" ] || [ "$choice" == "add ppa" ] || [ "$choice" == "ppa" ]; then
        clear
        # Specify PPA to add
        read -p "PPA to add (must be in form: ppa:<ppa name>/<subdirectory>)" ppa_add
        sudo add-apt-repository $ppa_add
        read -p "Press any key to continue..."
        
        # Remove no-longer-needed variables
        unset choice
        unset ppa_add
        
        # Loop back to main menu
        source /etc/app.sh
        
    # 6. Remove PPA
    elif [ "$choice" == "6" ] || [ "$choice" == "remove ppa" ]; then
        clear
        # Specify PPA to remove
        read -p "PPA to remove (must be in form: ppa:<ppa name>/<subdirectory>)" ppa_rem
        sudo add-apt-repository --remove $ppa_rem
        read -p "Press any key to continue..."
        
        # Remove no-longer-needed variables
        unset choice
        unset ppa_rem
        
        # Loop back to main menu
        source /etc/app.sh
        
    # 7. Generate Package List
    elif [ "$choice" == "7" ] || [ "$choice" == "generate package list" ] || [ "$choice" == "package list" ]; then
        clear
        # Generate package list, and place into /home/$USER/pkg-list
        sudo dpkg --get-selections > ~/pkg-list
        echo "Package list has been generated"
        echo "It is located at ~/pkg-list"
        read -p "Press any key to continue..."
        
        # Remove no-longer-needed variables
        unset choice
        
        # Loop back to main menu
        source /etc/app.sh
        
    # 8. Install from wget or dpkg
    elif [ "$choice" == "8" ]; then
        clear
        echo "1. wget"
        echo "2. dpkg"
        # Specify whether to use wget or dpkg
        read -p "Selection: " sel1
            # wget
            if [ "$sel1" == "1" ] || [ "$sel1" == "wget" ]; then
                clear
                echo "1. URL"
                echo "2. List of URLs"
                # Specify whether to use URL or List of URLs
                read -p "Selection: " sel2
                    # URL
                    if [ "$sel2" == "1" ] || [ "$sel2" == "URL" ] || [ "$sel2" == "url" ]; then
                        clear
                        # Specify extra parameters for wget
                        read -p "Enter 'wget' options/parameters: " wget_params
                        clear
                        # Specify URL for wget
                        read -p "Enter URL: " wget_url
                        wget $wget_params $wget_url
                    # List of URLs
                    elif [ "$sel2" == "2" ] || [ "$sel2" == "list" ]; then
                        clear
                        # Specify extra parameters for wget
                        read -p "Enter 'wget' options/parameters: " wget_params
                        clear
                        # Inform user to place list in /home/$USER/wget-list
                        echo "place the list of URLs in a file named wget-list in your "
                        echo "home directory: /home/$USER/wget-list"
                        read -p "Press any key to continue when file is in place..."
                        clear
                        echo "Running 'wget'"
                        # If ~/wget-pkgs does not exist, create it.
                        if [ ! -d "/home/$USER/wget-pkgs/" ]; then
                            sudo mkdir /home/$USER/wget-pkgs/
                        fi
                        # Run wget, and place all downloaded files into /home/$USER/wget-pkgs/
                        wget $wget_params -i /home/$USER/wget-list -P /home/$USER/wget-pkgs/
                    fi
            # dpkg
            elif [ "$sel1" == "2" ] || [ "$sel1" == "dpkg" ]; then
                clear
                echo "1. Install from .deb"
                echo "2. install from list"
                # Decide whether to use .deb or --set-selections
                read -p "Selection: " sel2
                    # If using .deb
                    if [ "$sel2" == "1" ] || [ "$sel2" == "deb" ] || [ "$sel2" == ".deb" ]; then
                        clear
                        # Specify path to .deb
                        read -p "Path to .deb file: " dpkg_path
                        clear
                        # Install from specified .deb
                        sudo dpkg -i $dpkg_path
                    # If using --set-selections
                    elif [ "$sel2" == "2" ] || [ "$sel2" == "list" ]; then
                        clear
                        # Specify path to list
                        read -p "Path to list: " dpkg_input
                        clear
                        # Mark changes according to $dpkg_input
                        sudo dpkg --set-selections < $dpkg_input
                        # Decide whether to install from marked changes
                        read -p "Install now? [y/n] " dpkg_install
                            # If yes, install
                            if [ "$dpkg_install" == "y" ] || [ "$dpkg_install" == "yes" ]; then
                                clear
                                sudo apt-get -u dselect-upgrade
                            fi
                    fi
            fi
        
        # Remove no-longer-needed variables
        unset choice
        unset sel1
        unset sel2
        unset wget_params
        unset wget_url
        unset dpkg_path
        unset dpkg_input
        unset dpkg_install
        unset install_method
        
        # Loop back to main menu
        source /etc/app.sh
        
    # 9. Backup important files
    elif [ "$choice" == "9" ] || [ "$choice" == "backup" ]; then
        clear
        
        # If /pref does not exist, create it
        sudo mkdir -v /pref
        # If /pref/etc does not exist, create it
        sudo mkdir -v /pref/etc
        # If /pref/etc/apt does not exist, create it
        sudo mkdir -v /pref/etc/apt
        
        # Backup /etc/bash.bashrc /etc/apt and /home/$USER(optional)
        sudo cp -v /etc/bash.bashrc /pref/etc
        sudo cp -R -v /etc/apt/ /pref/etc
        # Decide whether to backup /home/$USER
        read -p "Backup home directory? [y/n] " backup_home
            # If yes, backup home directory
            if [ "$backup_home" == "y" ]; then
                clear
                # If /pref/home does not exist, create it
                if [ ! -d "/pref/home" ]; then
                    sudo mkdir -v /pref/home
                fi
                # If /pref/home/$USER does not exist, create it
                if [ ! -d "/pref/home/$USER" ]; then
                    sudo mkdir -v /pref/home/$USER
                fi
                # backup /home/$USER
                sudo cp -R -v /home/$USER /pref/home/
            fi
        
        read -p "Press any key to continue... "
        clear
        echo "Backups are stored in /pref"
        echo ""
        read -p "Press any key to continue... "
        
        # Remove no-longer-needed variables
        unset choice
        unset backup_home
        
        # Loop back to main menu
        source /etc/app.sh
        
    # 10. Exit
    elif [ "$choice" == "10" ] || [ "$choice" == "exit" ] || [ "$choice" == "bash" ]; then
    
        # Remove no-longer-needed variables
        unset choice
        
        clear
        # Exit to a new bash shell
        bash
    
    # Unrecognized option
    else
        # Inform user that their selection is not recognized
        clear
        echo "Option is not recognized. Please enter a valid option... "
        echo ""
        read -p "Press any key to continue... "
        
        # Remove no-longer-needed variables
        unset choice
        
        # Loop back to main menu
        source /etc/app.sh
    
    fi
    
    
# Developed by:
#
# Tristan Williams        tristan401_2000@live.com        Main Developer
# Zealibib Slaughter        http://ubuntuforums.org/member.php?u=985458

# Changelog
#
# 1. Added option to generate package list.
# 2. Added functionality which allows user to type either the option number, or the option name, not just the number.
# 3. Added functionality which informs the user if they enter an unrecognized option.
# 4. Added option to clean up broken PPAs.
# 5. Fixed bug which caused variables to remain set after script execution.
# 6. Added option to make backups of important system files/directories.
# 7. Added option to search for packages.
# 8. Added option to install from wget or dpkg.
# 9. Added commentary.


```

The initial menu looks like this:
```

1. maintenance
2. install software
3. remove software
4. Search for a package
5. add ppa
6. remove ppa
7. generate package list
8. install from wget or dpkg
9. Backup important files
10. exit
Selection: 

```

---

### Post by zealibib slaughter on 2013-12-30
maybe add a way to clean up broken ppa's something like

```


echo "Please wait checking system for broken ppa's"

sudo apt-get update > update.txt

clear

cat update.txt | grep Err | cut -c 12- > broken.txt 

IFS=$'\n' read -d '' -r -a lines < broken.txt
 
echo "Found the following broken ppa's"
echo "${lines[@]}"
echo "It may be that the repositories are down and will be up later"
echo "If you continue these will be deleted from your system"



read -p "Continue (y/n)?" CONT
if [ "$CONT" == "y" ]; then
  
cat update.txt | grep Err | cut -c 12- | cut -d ' ' -f 1 > broken.txt 

IFS=$'\n' read -d '' -r -a lines < broken.txt

i="0"

while [[ "${lines[$i]}" != "" ]] 
do
    
     grep -H "${lines[$i]}" /etc/apt/sources.list.d/*.list | cut -d ':' -f 1  > delete.txt
    IFS=$'\n' read -d '' -r -a linesd < delete.txt
    a="0"
    while [[ "${linesd[$a]}" != "" ]]
do

file="${linesd[$a]}"
if [ -f "$file" ]
then
clear
    echo "$file will be removed."
read -p "Continue (y/n)?" CONT
if [ "$CONT" == "y" ]; then
  echo "Removing $file";
  #sudo rm "$file"
sleep 5

else
  echo "Will keep $file";
sleep 5

fi
else
    echo "$file not found."
sleep 5
fi

    echo "${linesd[$a]}"
a=$[$a+1]
    done
   

i=$[$i+1]
done
else
  echo "Will exit now";
fi
echo "exiting"
rm update.txt
rm broken.txt
rm delete.txt



```

btw the dangerous part of this is commented out. I didn't feel it was too wise to keep a loaded gun just lying around unsupervised.

---

### Post by Vaphell on 2013-12-31
i'd consider creating menu using *select* instead of reinventing the wheel.

```

menu=(
       "maintenance"
       "install software"
       "remove software"
       "search for a package"
       "add ppa"
       "remove ppa"
       "generate package list"
       "backup important files"
       "exit"
     )

PS3="Your choice: "
select choice in "${menu[@]}"
do
  break
done
echo "You picked '$choice' ($REPLY)" 

```
result
```
$ ./menu.sh 
1) maintenance		   6) remove ppa
2) install software	   7) generate package list
3) remove software	   8) backup important files
4) search for a package	   9) exit
5) add ppa
Your choice: 6
You picked 'remove ppa' (6)

```

select is a loop that allows for infinite repetition, so depending on your needs *break* may or may not be required


i'd also put stuff in functions, so the main condition testing is not a convoluted mess spanning multiple pages of code, but something like 

```

function_1()
{
  ...
}
function_2()
{
  ...
}
function_3()
{
  ...
}

if condition1
  function_1
elif condition2
  function_2
elif condition3
  function_3
fi
```



@zealibib slaughter
```
a=$[$a+1]
```
this syntax is deprecated, use a=$((a+1)) or simply ((a++))

```
IFS=$'\n' read -d '' -r -a linesd < delete.txt
```
that's what *readarray* is for
```
readarray -t lines < file
```

---

### Post by Tristan_Williams on 2013-12-31
@Vaphell
I attempted to follow your suggestion but a few things prevented me from using 'select' and 'function()'

1. My level of bash expertise (this project is mainly for learning experience)
2. I couldnt figure out how to put multi-word options in select.

It would be great if you could format the code to using 'select' and 'function()', however I don't expect you to do that for me haha.

---

### Post by steeldriver on 2013-12-31
I'd actually started sketching out a version using 'select' before Vaphell posted - maybe this will help (note that it *does* loop until the 'exit' option is selected - which may not be what you want - you can use Vaphell's suggestion of making the 'do' action into a 'break' and then just executing a single case)

I've cut it down to 3 actions + exit for clarity

```

#!/bin/bash

action_list=( "maintenance" "install software" "remove software" "exit" )

function do_maint {
  echo "Performing system maintenance"
}

function do_inst {
  echo "Installing software"
}

function do_uninst {
  echo "Removing software"
}

# the main select loop
select action in "${action_list[@]}"
do
  case "$REPLY" in

  1) do_maint
  ;;

  2) do_inst
  ;;

  3) do_uninst
  ;;

  4) exit 0
  ;;

  *) echo "Please choose a number from 1 to ${#action_list[@]}"
  ;;

  esac
done

```

---

### Post by Tristan_Williams on 2013-12-31
Thanks for all the replies so far. 
Any ideas for additional options?

---

