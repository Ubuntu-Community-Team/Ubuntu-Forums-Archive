---
title: "Command to check list of packages installed in ubuntu host system"
date: 2023-05-09
forum: General Help
---

### Post by appusony on 2023-05-09
Dear All,

I wanted to compare the software packages that is installed in my system & in my collegues system, which could be of same ubuntu OS version or different Ubuntu OS version, may I know please, the best command or the the best way to search & compare the list of software packages installed in this different systems?

Many thanks in advance,

Best Wishes,

---

### Post by Tadaen_Sylvermane on 2023-05-09
```
apt list | grep installed | cut -d\/ -f 1
```

Pipe that to a file and parse it.

*EDIT*

Another option.

```
dpkg --get-selections
```

---

### Post by TheFu on 2023-05-09
If you want to get the exact version for each package too, not just the main package name, 
**dpkg -l**

That's for APT.
For flatpaks and snaps, you'll need to use those tools' methods ... usually something like "snap list" 

Redirect the text output to a file (do this on both systems), then bring the different files to 1 system and use a file compare tool ... **diff**, **sdiff**, **meld**, whatever you like, to see the differences.  If the package lists aren't sorted, could be useful to **sort** them before the comparison.  I don't think **sort**-ing is needed, but YMMV.

---

### Post by MAFoElffen on 2023-05-09
Run the [UbuntuForums 'system-info' Script]("https://github.com/UbuntuForums/system-info") in my signature line. Approved and endorsed by the Forum. Near the end of the generated report, is sections for all manually installed packages (beyond what was installed as the initial install), Snaps and FlatPak package lists.

Safe, efficient... Then the only command you have to remember is to start the script...

---

### Post by appusony on 2023-05-09
Thanks Infinity , Love you all!

May I know please, after running system-info script - This is the section "[COLOR=#000000] --- User Installed Package List:" that I need to look for the packages that I have explicitly installed in my ubuntu's host machine, am I correct please? & may I know please, what is the section name that I need to look for initial install ie., "[/COLOR][COLOR=#000000]beyond what was installed as the initial install"?[/COLOR]

---

### Post by MAFoElffen on 2023-05-10
The code is:
```

function GetUserInstalled()
{
    ## Get a list of User Installed Packages 
    # This only works for Debian Branch...
        
    echo -e "   --- User Installed Package List:"
    # check if Debian Branch. Otherwise 'apt-mark' will not be found...
    if [[ "$debian_branch" == "0" ]]
    then    
        manually_installed=$(mktemp /tmp/ManuallyInstalled-XXXXX)
        default_installed=$(mktemp /tmp/DefaultInstalled-XXXXX)
        user_installed=$(mktemp /tmp/UserInstalled-XXXXX)
        # Use apt-mark to list all packages marked as manually installed. 
        apt-mark showmanual | sort -u > $manually_installed
        # Check to see if defualt installed list exists
        # for prebuilt system images, it does not exist
        if [ -f /var/log/installer/initial-status.gz ]
        then 
            # Get the list of default installed packages at initial installation.
            gzip -dc /var/log/installer/initial-status.gz 2> /dev/null | \
                sed -n 's/^Package: //p' | \
                sort -u > $default_installed
        else 
            touch $default_installed
        fi
        # Use compare, to exclude those defaults that are unique, AND exclude defaults 
        # that are presently marked as manually installed. (Those 'may' have been changed.)  
        comm -23 $manually_installed $default_installed > $user_installed
        # Print the list in two columns
        awk 'NF' $user_installed #\ Removed 2022.03.10 to turn to one column
        #| pr -2T  # You can remove the pr filter on this to keep output in a single column...
        nl # Add newline in report
        # Remove the temporary files
        rm -f $manually_installed
        rm -f $default_installed
        rm -f $user_installed
    else
        echo -e "The system tested is not in the Debian Branch. "
        echo -e "The method written in this script is for Debian Branch conventions."
        nl
    fi
    unset -v manually_installed default_installed user_installed
}

```
I commented the code so people could follow the logic... 

On an initial installation from an installer, file '/var/log/installer/initial-status.gz' contains a list of all the packages that are installed in the initial installation.

The section in the report is labeled as "   --- User Installed Package List:"

EDIT: If you search on my Forum posts, there's a few times I posted a one liner I came up with to do the same thing from the command line, but it is long, hard to type out and sometimes got errors. The function I came up later from that, checks for different conditions, so adds error control for those conditions.

---

### Post by appusony on 2023-05-10
Thanks a lot once again, highly appreciate for your help!

Sorry for my understandings please, some clarification onto the below:


1. >> "[COLOR=#000000]'/var/log/installer/initial-status.gz' contains a list of all the packages that are installed in the initial installation."

So by this statement -> it means that list of packages that got installed , while installing fresh Ubuntu OS - is my understanding is right please? or is it the packages that got installed , that might be needed by "[/COLOR][COLOR=#000000]system-info script"?

2. >> [/COLOR][COLOR=#000000]The section in the report is labeled as " --- User Installed Package List:"

so by this statement -> it means that the list of packages that I manually installed, after Ubuntu OS installation, am I correct please?[/COLOR]

---

### Post by MAFoElffen on 2023-05-11
> **appusony said:**
> Thanks a lot once again, highly appreciate for your help!

Sorry for my understandings please, some clarification onto the below:


1. >> "[COLOR=#000000]'/var/log/installer/initial-status.gz' contains a list of all the packages that are installed in the initial installation." [/COLOR][COLOR=#000000]

So by this statement -> it means that list of packages that got installed , while installing fresh Ubuntu OS - is my understanding is right please? [/COLOR]**[COLOR=#ff0000](<< Yes)[/COLOR]**[COLOR=#000000] or is it the packages that got installed , that might be needed by "[/COLOR][COLOR=#000000]system-info script"? [/COLOR][COLOR=#ff0000]**(<< No)**[/COLOR][COLOR=#000000]

2. >> [/COLOR][COLOR=#000000]The section in the report is labeled as " --- User Installed Package List:"

so by this statement -> it means that the list of packages that I manually installed, after Ubuntu OS installation, am I correct please?[/COLOR] **[COLOR=#ff0000](<< Yes)[/COLOR]** 
Answered in [COLOR=#ff0000]**red**[/COLOR] above...

---

### Post by appusony on 2023-05-11
Perfect! Thanks Infinity!

---

