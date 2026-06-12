---
title: "builtin: not found. when running shell file."
date: 2013-08-04
forum: General Help
---

### Post by 3wais on 2013-08-04
[COLOR=#000000][FONT=Verdana]During installation of a program. this error occured :[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
```
./admin/install/bin/install_customdesigner: 1: ./admin/install/bin/install_customdesigner: builtin: not found
```[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I searched a bit about this. I understood what it means. I even tried to run some commands preceeded by builtin and they worked fine.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]but in that shell script they don't. here are the lines that include builtin in the script:[/FONT][/COLOR]
```
# No $() construct is used in order to stay compatible with POSIX shellsnps_PKG_INSTL_PLC=`builtin cd \`$DIRNAME $0\` && builtin cd ../../../ && builtin pwd`
if [ $? -ne 0 ]; then $ECHO "$PROGNAME: Error: could not expand installation path. Exiting."; exit 1; fi


SRC_ENV_FILE=${snps_PKG_INSTL_PLC}/bin/.wrapper.sh
$CHMOD 0755 $SRC_ENV_FILE


if [ $? -ne 0 ]; then $ECHO "$PROGNAME: Warning: failed to set execute permissions for $SRC_ENV_FILE. Please run chmod 755 $SRC_ENV_FILE manually."; fi


# Checking for available platforms
AVAILABLE_PLATFORMS=
if [ -d "$snps_PKG_INSTL_PLC/amd64" ]; then
    AVAILABLE_PLATFORMS='amd64'
    if [ -e "$snps_PKG_INSTL_PLC/suse64" ]; then
        if [ -L "$snps_PKG_INSTL_PLC/suse64" ]; then
            echo "'suse64'  link  is  already  created.  To reassign."
            $RM -f $snps_PKG_INSTL_PLC/suse64
            `builtin cd $snps_PKG_INSTL_PLC; $LN -s -f ./amd64 suse64`
        fi
    else
        `builtin cd $snps_PKG_INSTL_PLC; $LN -s -f ./amd64 suse64`
    fi
fi
if [ -d "$snps_PKG_INSTL_PLC/linux" ]; then
    AVAILABLE_PLATFORMS="$AVAILABLE_PLATFORMS linux"
    if [ -e "$snps_PKG_INSTL_PLC/suse32" ]; then
        if [ -L "$snps_PKG_INSTL_PLC/suse32" ]; then
            echo "'suse32'  link  is  already  created.  To reassign."
            $RM -f $snps_PKG_INSTL_PLC/suse32
            `builtin cd $snps_PKG_INSTL_PLC; $LN -s -f ./linux suse32`
        fi
    else
        `builtin cd $snps_PKG_INSTL_PLC; $LN -s -f ./linux suse32`
    fi
fi
if [ -z "$AVAILABLE_PLATFORMS" ]; then $ECHO "$PROGNAME: Error: no binary installations found. Exiting."; exit 1; fi 


builtin cd ${snps_PKG_INSTL_PLC}/bin
if [ $? -ne 0 ]; then $ECHO "$PROGNAME: Error: could not change to '${snps_PKG_INSTL_PLC}/bin directory'. Exiting."; exit 1; fi


WRAPPER_NAME=".wrapper.sh"


for snps_PLATFORM in $AVAILABLE_PLATFORMS 
do


    PLATFORM_DIR=${snps_PKG_INSTL_PLC}/$snps_PLATFORM


    if [ -d ${PLATFORM_DIR}/qt/plugins/imageformats ]; then
        `builtin cd ${PLATFORM_DIR}/platform/bin; $LN -sf ../../../$snps_PLATFORM/qt/plugins/imageformats .`
        if [ $? -ne 0 ]; then $ECHO "$PROGNAME: Warning: could not create symbolic link."; fi
    fi


    [ -d ${PLATFORM_DIR}/platform/bin ] || continue


    for snps_fl in `$LS ${PLATFORM_DIR}/platform/bin`
    do
        snps_fl=`$BASENAME $snps_fl`


        if [ ! -d ${PLATFORM_DIR}/platform/bin/$snps_fl ]; then
            if [ ! -f $snps_fl ]; then
                $LN -s ./${WRAPPER_NAME} $snps_fl
                if [ $? -ne 0 ]; then $ECHO "$PROGNAME: Warning: could not create symbolic link."; fi
            fi
        fi
    done
    [ -d ${PLATFORM_DIR}/OA/bin ] || continue




    for snps_fl in `$LS ${PLATFORM_DIR}/OA/bin`
    do
        snps_fl=`$BASENAME $snps_fl`


        if [ ! -L ${PLATFORM_DIR}/OA/bin/$snps_fl ]; then
            if [ ! -d ${PLATFORM_DIR}/OA/bin/$snps_fl ]; then
                if [ ! -f $snps_fl ]; then
                    $LN -s ./${WRAPPER_NAME} $snps_fl
                    if [ $? -ne 0 ]; then $ECHO "$PROGNAME: Warning: could not create symbolic link."; fi
                fi
            fi


        fi


    done




    if [ -f ${PLATFORM_DIR}/ext/bin/StarXtract_oa ]; then
        if [ ! -f StarXtract_oa ]; then
            $LN -sf ./${WRAPPER_NAME} StarXtract_oa  
            if [ $? -ne 0 ]; then $ECHO "$PROGNAME: Warning: could not create symbolic link. "; fi
        fi
    fi


done




exit 0
```

howto fix this ??

---

### Post by Paddy Landau on 2013-08-04
You shouldn't have to use *builtin* within a script. Just use *cd* as normal.

Why are using *builtin*? Perhaps if we understand why, we can help.

---

