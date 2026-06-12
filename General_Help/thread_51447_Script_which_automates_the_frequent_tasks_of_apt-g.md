---
title: "Script which automates the frequent tasks of apt-get"
date: 2005-07-24
forum: General Help
---

### Post by ghostintheshell on 2005-07-24
Thanks for your feedback!

 ```

#!/bin/sh

TITLE="=== DEBIAN UPDATE MANAGER ==="
AUTHOR="@2005-07 ghostintheshell"
VERSION="v.2005.09.29"
##### To do:
##### - the to do list o_0'

### DECLARATIONS
### ------------

## OPTIONS (system)

#the sources file
SOURCES="/etc/apt/sources.list"

#editor to use
EDITOR="gedit"
EDITORPATH=$(which $EDITOR)    #'which' returns the full path of the selected editor

#apt-get
APTGET="apt-get"
APTGETPATH=$(which $APTGET)

## OPTIONS (script)

#verbose mode?
VERBOSE=1    #0 for silent, 1 for verbose

#debug mode?
DEBUG=0        #0 for normal, 1 for debug

## CONSTANTS

#break options
WAIT=1        #wait for a user action
NOWAIT=0    #just display a break

## PUBLIC DECLARATIONS
gsPossibilities=""
gsPossibilitiesDefault=""
gsAnswer=""

### FUNCTIONS
### ---------

##

function displayDEBUG() {
    if [ $DEBUG -eq 1 ]; then echo "[DEBUG] $1"; fi
}

function displayMESSAGE() {
    if [ $VERBOSE -eq 1 ]; then echo "==> $1 ..." && echo; fi
}

function displayERROR() {
    echo "[ERROR] $1"
}

function displayBREAK() {
    echo
    if [ $1 -eq 1 ]; then echo -n "--- Press <ENTER> to continue ---"; read foo; echo; fi
}

##

function editSources() {
    iError=0
    displayMESSAGE "Opening the sources list with $EDITOR"
    $EDITORPATH $SOURCES > /dev/null 2>&1

    if [ $? -ne 0 ]; then
        iError=1
        displayERROR "Please check your parameters!"
        displayERROR "Editor = \"$EDITOR\""
        sMoreHelp=""; if [ -z $EDITORPATH ]; then sMoreHelp=" !!! not found !!!"; fi
        displayERROR "Editor path = \"$EDITORPATH\"$sMoreHelp"
        sMoreHelp=""; if [ ! -e $SOURCES ]; then sMoreHelp=" !!! not found !!!"; fi
        displayERROR "Sources file = \"$SOURCES\"$sMoreHelp"
        displayBREAK $WAIT
    fi
    return $iError
}

function updatePackageslist() {
    displayMESSAGE "Updating"
    apt-get update
}

function simulatePackages() {
    iNewPackage=1
    displayMESSAGE "Doing simulation"
    if [ $VERBOSE -eq 1 ]; then
        apt-get upgrade --simulate --show-upgraded
    else
        apt-get upgrade --simulate
    fi
    
    sNewPackage="$(apt-get dist-upgrade -s |  grep "newly installed" | grep "[1-9]")"
    if [ -z "$sNewPackage" ]; then iNewPackage=0; fi
    return $iNewPackage
}

function upgradePackages() {
    displayMESSAGE "Upgrading"
    if [ $VERBOSE -eq 1 ]; then
        apt-get upgrade --show-upgraded
    else
        apt-get upgrade
    fi
}

function checkDependencies() {
    displayMESSAGE "Checking dependencies"
    apt-get check
}

function cleanOldarchives() {
    displayMESSAGE "Cleaning old archives"
    apt-get autoclean
}

##

function writeQuestionOrInfo {
    echo
    case $1 in
    "A")
        echo -n "[1/5] Edit the sources list ($SOURCES) [y(es)/N(o)/e(x)it]?"
        gsPossibilities="ynx"; gsPossibilitiesDefault="n"
        ;;
    "B")
        echo -n "[2/5] Update the list of available packages [Y(es)/n(o)/(r)estart/e(x)it]?"        
        gsPossibilities="ynrx"; gsPossibilitiesDefault="y"
        ;;
    "C")
        echo -n "[3/5] Proceed to an upgrade simulation [C(ontinue)/(r)estart/e(x)it]?"
        gsPossibilities="cbrx"; gsPossibilitiesDefault="c"
        ;;
    "D1")
        echo -n "[4/5] Proceed to upgrade [Y(es)/n(o)/(r)estart/e(x)it]?"
        gsPossibilities="ynrx"; gsPossibilitiesDefault="y"
        ;;
    "D2")
        echo    "[4/5] No need to upgrade! [C(ontinue)]"
        ;;
    "E")
        echo -n "[5/5] Quit [e(X)it/(r)estart/(m)ore]?"
        gsPossibilities="xrm"; gsPossibilitiesDefault="x"
        ;;
    "M1")
        echo -n "[+] Check dependencies [Y(es)/n(o)/(r)estart/e(x)it]?"
        gsPossibilities="ynrx"; gsPossibilitiesDefault="y"
        ;;
    "M2")
        echo -n "[+] Clean old archives [Y(es)/n(o)/(r)estart/e(x)it]?"
        gsPossibilities="ynrx"; gsPossibilitiesDefault="y"
        ;;
    *)
        ;;
    esac
}

function readAnswer {
    while :
    do
        echo -n " "; read sInput

        if [ "$sInput" = "" ]; then sInput=$gsPossibilitiesDefault; fi  #default answer if empty answer detected
        if [ "${#sInput}" -ne 1 ]; then sInput="dummy"; fi                #answer length must be only 1 character!

        if echo $1 | grep -q "$sInput"; then
            gsAnswer=$sInput; break
        else
            echo -n "WTF!?"
        fi
        
    done
}

function executeAction {

    let iReturn=0
    
    case $1 in
    "A")
        writeQuestionOrInfo $1;    readAnswer $gsPossibilities
        case $gsAnswer in
        "y"|"Y") 
            editSources; iReturn=$?
            ;;
        esac
        ;;
    "B")
        writeQuestionOrInfo $1; readAnswer $gsPossibilities
        case $gsAnswer in
        "y"|"Y")
            updatePackageslist
            ;;
        esac
        ;;
    "C")
        writeQuestionOrInfo $1; readAnswer $gsPossibilities
        case $gsAnswer in
        "c"|"C")
            simulatePackages; iReturn=$?
            ;;
        esac
        ;;
    "D1")
        writeQuestionOrInfo $1; readAnswer $gsPossibilities
        case $gsAnswer in
        "y"|"Y")
            upgradePackages
            ;;
        esac
        ;;
    "D2")
        writeQuestionOrInfo $1;
        ;;
    "E")
        writeQuestionOrInfo $1; readAnswer $gsPossibilities
        case $gsAnswer in
        "m"|"M")
            iReturn=253
            ;;
        esac
        ;;
    "M1")
        writeQuestionOrInfo $1; readAnswer $gsPossibilities
        case $gsAnswer in
        "y"|"Y")
            checkDependencies
            ;;
        esac
        ;;
    "M2")
        writeQuestionOrInfo $1; readAnswer $gsPossibilities
        case $gsAnswer in
        "y"|"Y")
            cleanOldarchives
            ;;
        esac
        ;;
    esac

    case $gsAnswer in
    "x"|"X"|"q"|"Q")
        iReturn=255    #exit
        ;;
    "r"|"R") 
        iReturn=254    #restart
        ;;
    esac

    return $iReturn
}

### MAIN
### ----

#welcome buddy
clear; echo -e "$TITLE ($VERSION)\n"
let iContinue=0

#some verifications
if [ -z $APTGETPATH ]; then 
    let iContinue=99
    displayERROR "Sorry $APTGET is not found on this system!"
    displayBREAK $WAIT
fi
    
#go for it
if [ $iContinue -eq 0 ]; then
    while : 
    do

        if [ $iContinue -eq 0 ]; then
            clear; echo -e "$TITLE ($VERSION)\n\nUsing $($APTGET -v | grep "apt")"
            let iContinue=1
        fi
        
        #[A] Edit the sources list?
        if [ $iContinue -eq 1 ]; then
            executeAction "A"
            case $? in
                255) break;;
                254) iContinue=0;;
                1)  iContinue=0;;
            esac
        fi

        #[b] Update
        if [ $iContinue -eq 1 ]; then
            executeAction "B"
            case $? in
                255) break;;
                254) iContinue=0;;
            esac
        fi

        #[C] Proceed to upgrade simulation?
        if [ $iContinue -eq 1 ]; then
            let iNewPackage=0
            executeAction "C"
            case $? in
                255) break;;
                254) iContinue=0;;
                1) iNewPackage=1;;
            esac
        fi

        #[D] Proceed to upgrade?
        if [ $iContinue -eq 1 ]; then
            if [ $iNewPackage -eq 1 ]; then
                executeAction "D1"
                case $? in
                    255) break;;
                    254) iContinue=0;;
                esac
            else
                executeAction "D2"
            fi
        fi

        #[+] More options #1 (Check dependencies)?
        if [ $iContinue -eq 2 ]; then
            executeAction "M1"
            case $? in
                255) break;;
                254) iContinue=0;;
            esac
        fi

        #[+] More options #2 (Clean old archives)?
        if [ $iContinue -eq 2 ]; then
            executeAction "M2"
            case $? in
                255) break;;
                254) iContinue=0;;
            esac
        fi

        #[E] Quit?
        if [ $iContinue -eq 1 ] || [ $iContinue -eq 2 ]; then
            executeAction "E"
            case $? in
                255) break;;
                254) iContinue=0;;
                253) iContinue=2;;
            esac
        fi    
        
    done
fi

#see you buddy
echo; echo "Bye ..."; echo

```

---

