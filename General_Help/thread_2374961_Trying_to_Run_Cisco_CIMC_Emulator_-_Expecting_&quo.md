---
title: "Trying to Run Cisco CIMC Emulator - Expecting &quot;fi&quot; error when running network.sh"
date: 2017-10-20
forum: General Help
---

### Post by ziomek1985 on 2017-10-20
Hello.  I'm not a coder but I understand how to make changes to code in script files.  I installed Ubuntu to run this Cisco CIMC 3.0 Emulator for my studies from [https://communities.cisco.com/docs/DOC-71619](https://communities.cisco.com/docs/DOC-71619).  The presenter used Red Hat 6.5 but I want to use Ubuntu.  Basically you download a zip file with bunch of files from that link.  You extract the files.  Install tuncl and bridge utils ([COLOR=#333333][FONT=UbuntuMono]sudo apt-get install uml-utilities bridge-utils).

[/FONT][/COLOR]After that it tells u to run this network.sh file as root and I get this error message

```

"This script creates/removes network mode for emulator"
./network.sh: 37: ./network.sh: Syntax error: "(" unexpected (expecting "fi")

```

Here is what's inside network.sh.  Any help is appreciated.  Thank you

```


#!/bin/sh


if [ "$(id -u)" != "0" ]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi


echo "This script creates/removes network mode for emulator"


which tunctl > /dev/null 2>&1


if [ $? -eq 1 ];then
  echo "tunctl command not found to create tap network"
  echo "Install required package and re-run this script"
  exit 1
fi


DHCP_Support_Enabled=0
Dont_set_IP_for_tap=0
tap_interface=""
Bridge_name="Emulator-Bridge"


is_network_interface_exists ()
{
    ifconfig $1 > /dev/null 2>&1
    return $?
}


is_valid_IP_address()
{
    local  ip=$1
    local  stat=1


    if [[ $ip =~ ^[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}$ ]]; then
        OIFS=$IFS
        IFS='.'
        ip=($ip)
        IFS=$OIFS
        [[ ${ip[0]} -le 255 && ${ip[1]} -le 255 \
            && ${ip[2]} -le 255 && ${ip[3]} -le 255 ]]
        stat=$?
    fi
    return $stat
}




is_bridge_ip_valid()
{
    is_valid_ip=1
    # Cent OS 6.5 start IP address as "inet addr:10.127.133.77 Bcast:10.127.133.25 Mask:255.255.255.0" - So grep for "inet addr:"
    ipaddress=$(ifconfig $Bridge_name | awk -F"[: ]+" '/inet addr:/ {print $4}')
    if [ -n "$ipaddress" ]; then
        is_valid_IP_address $ipaddress
        is_valid_ip=$?
        return $is_valid_ip
    fi


    # RHEL 7.0 start IP address as "inet 10.127.133.77 netmask 255.255.255.0 broadcast 10.127.133.25 " - So grep for "inet"
    ipaddress=$(ifconfig $Bridge_name | grep -w inet | awk {'print $2'})
    if [ -n "$ipaddress" ]; then
        is_valid_IP_address $ipaddress
        is_valid_ip=$?
    fi


    return $is_valid_ip
}


create_bridge_interface ()
{
    PATH=$PATH:/usr/sbin:/sbin
    echo "Creating bridge network "


    which brctl > /dev/null 2>&1


    if [ $? -eq 1 ];then
      echo "brctl command not found to create bridge network"
      echo "Install required package and re-run this script"
      exit 1
    fi


    is_network_interface_exists $Bridge_name
    if [ $? -ne 0 ];then
        brctl addbr $Bridge_name
    fi    
    tap_interface_support
    if [ -n $tap_interface ]; then
        ifconfig $tap_interface up
        brctl addif $Bridge_name $tap_interface
    else
            echo "tap interface name is empty"
        exit 1
    fi
    #
    # First take physical ethernet interface down, then bring it up with IP address 0.0.0.0 - This is to avoid network traffic on eth interface
    #
    ifdown $1 > /dev/null 2>&1
    ifconfig $1 0.0.0.0 promisc up


    brctl addif $Bridge_name $1 > /dev/null 2>&1    
    
    if [ $DHCP_Support_Enabled -eq 1 ];then
        echo "Discovering IP for bridge network..."
        dhclient -r $Bridge_name
        dhclient $Bridge_name > /dev/null 2>&1
        
    else


        while true; do
            read -p "Enter static IP address for Bridge network :" bridge_ip
            is_valid_IP_address $bridge_ip
            if [ $? -ne 0 ];then
                echo " $bridge_ip is not vaild IP address"
                continue
            fi
            break
        done
        
        while true; do
            read -p "Enter broadcast address for Bridge network :" broad_cast_ip
            is_valid_IP_address $broad_cast_ip
            if [ $? -ne 0 ];then
                echo " $broad_cast_ip is not vaild IP address"
                continue
            fi
            break
        done
        
        while true; do
            read -p "Enter netmask value for Bridge network :" netmask
            is_valid_IP_address $netmask
            if [ $? -ne 0 ];then
                echo " $netmask is not vaild IP address"
                continue
            fi
            break
        done
        
        while true; do
            read -p "Enter default gateway address for Bridge network :" gateway
            is_valid_IP_address $gateway
            if [ $? -ne 0 ];then
                echo " $gateway is not vaild IP address"
                continue
            fi
            break
        done
        
        ifconfig $Bridge_name $bridge_ip netmask $netmask broadcast $broad_cast_ip up
            if [ $? -ne 0 ];then
                echo " Assigning IP address to bridge interface is failed"
                exit 1
            fi
        route add default gw $gateway    
        get_ip_for_emulator        
    
    fi
    
    is_bridge_ip_valid
    if [ $? -eq 1 ]; then
        if [ $DHCP_Support_Enabled -eq 1 ];then
            echo "Could not discover IP for bridge network, DHCP server may be unavailable"
        else
            echo "Bridge IP is not valid"
        fi
        Remove_bridge_network $1
        exit 1
    fi
    
    ifconfig $Bridge_name up
            
}


DHCP_Support ()
{
    read -p "Enter host Ethernet interface name to connect to bridge [e.g eth0] :" interface
    is_network_interface_exists $interface
    if [ $? -ne 0 ];then
    echo "$interface does not exist on host"
    exit 1
    fi
    create_bridge_interface $interface
    echo "Bridge network is created successfully,now launch emulator"
}




tap_interface_support()
{
    while true; do
        read -p "Enter tap interface name [e.g tap0] :" tap_interface
        is_network_interface_exists $tap_interface
        if [ $? -eq 0 ];then
            read -p "tap interface $tap_interface already exists , override ?[y/n] :" yn
            case $yn in
            [Yy]* ) break;;
            [Nn]* ) continue;;
            * ) echo "Please answer yes or no.";;
                esac
        fi
        break
    done
    tunctl -t $tap_interface -u `id -un` -g `id -gn`
    sed -i -e 's/ifname=.*/ifname='$tap_interface' $PACKET_LOG"/g' *_cimc.sh
    if [ $Dont_set_IP_for_tap -eq 1 ] ; then 
        return 0
    else
        while true; do
            read -p "Enter IP address for $tap_interface [e.g:192.168.1.10] :" tap_ip
            is_valid_IP_address $tap_ip
            if [ $? -ne 0 ];then
                echo " $tap_ip is not vaild IP address"
                continue
            fi
            sudo /sbin/ifconfig $tap_interface $tap_ip
            if [ $? -ne 0 ];then
                echo " Assigning IP address to $tap_interface interface is failed"
                exit 1
            fi
            break
        done
        get_ip_for_emulator
    fi
    echo "Tap network is created successfully,now launch emulator"
}


get_ip_for_emulator()
{
    
    echo "Existing emulator static IP details from configuration file"
    echo "IP address = $(cat UCSC-*-Config.ini | grep "BMC_IP" | cut -d'=' -f2)"
    echo "Broad cast address = $(cat UCSC-*-Config.ini | grep "BMC_BROADCAST_IP" | cut -d'=' -f2)"
    echo "Netmask value = $(cat UCSC-*-Config.ini | grep "BMC_NETMASK" | cut -d'=' -f2)"
    echo "Default Gateway address = $(cat UCSC-*-Config.ini | grep "BMC_GATEWAY_IP" | cut -d'=' -f2)"
    read -p "Do you want to change existing configuration [y/n]" option
    if [ "$option" == 'y' ] || [ "$option" == 'Y' ] || [ "$option" == "yes" ] || [ "$option" == "YES" ];then
        while true; do
            read -p "Enter Static IP address for emulator :" emulator_ip
            is_valid_IP_address $emulator_ip
            if [ $? -ne 0 ];then
                echo " $emulator_ip is not vaild IP address"
                continue
            fi
            break
        done
        
        sed -i 's/^BMC_IP.*/BMC_IP = '$emulator_ip'/' *-Config.ini
        
        while true; do
            read -p "Enter broadcast address for emulator :" broad_cast_ip
            is_valid_IP_address $broad_cast_ip
            if [ $? -ne 0 ];then
                echo " $broad_cast_ip is not vaild IP address"
                continue
            fi
            break
        done
        
        sed -i 's/^BMC_BROADCAST_IP.*/BMC_BROADCAST_IP = '$broad_cast_ip'/' *-Config.ini
        
        while true; do
            read -p "Enter netmask value for emulator :" netmask
            is_valid_IP_address $netmask
            if [ $? -ne 0 ];then
                echo " $netmask is not vaild IP address"
                continue
            fi
            break
        done
        
        sed -i 's/^BMC_NETMASK.*/BMC_NETMASK = '$netmask'/' *-Config.ini
        
        while true; do
            read -p "Enter default gateway address for emulator :" gateway
            is_valid_IP_address $gateway
            if [ $? -ne 0 ];then
                echo " $gateway is not vaild IP address"
                continue
            fi
            break
        done
        
        sed -i 's/^BMC_GATEWAY_IP.*/BMC_GATEWAY_IP = '$gateway'/' *-Config.ini
    fi


}


Remove_tap_network()
{
  
    read -p "Enter tap interface name to remove [e.g tap0] :" tap_interface
    is_network_interface_exists $tap_interface
    if [ $? -eq 0 ];then
        ifconfig $tap_interface down
        if [ $? -ne 0 ];then
            echo "Removing $tap_interface failed"
        fi
        tunctl -d $tap_interface > /dev/null 2>&1
        if [ $? -ne 0 ];then
            echo "Removing $tap_interface failed"
           else
            echo "Successfully removed $tap_interface"
        fi        
    else
        echo "$tap_interface does not exist on host"
        exit 1
    fi
    
}


Remove_bridge_network()
{
    is_network_interface_exists $Bridge_name
    if [ $? -ne 0 ];then
       echo "$Bridge_name does not exist on host"
       exit 1
    fi
    if [ -n "$1" ]; then
        eth_interface=$1
    else
            read -p "Enter previously attched physical ethernet interface name to bring back to normal mode :" eth_interface
    fi
    
    is_network_interface_exists $eth_interface
    if [ $? -eq 0 ];then
    
        brctl show | grep -w $eth_interface > /dev/null 2>&1
        if [ $? -eq 0 ]; then
            ifdown $eth_interface
        else
            echo "$eth_interface is not connected to bridge"
            exit 1
        fi
    
    else
        echo "$eth_interface does not exist on host"
        exit 1
    fi


    ifconfig $Bridge_name down 
    if [ $? -ne 0 ];then
       echo "Removing $Bridge_name failed"
    fi
    brctl delbr $Bridge_name
    if [ $? -ne 0 ];then
       echo "Removing $Bridge_name failed"
    else
       echo "Successfully removed $Bridge_name"
    fi
    # 
    # bring up physical ethernet inteface to "normal" mode 
    #
    ifconfig $eth_interface -promisc > /dev/null 2>&1
    ifup $eth_interface > /dev/null 2>&1
}


show_help_content()
{
  echo "The network.sh script is used to create tap or bridge network interface on host machine to communicate with emulator.
  
1-Tap Network:


    Tap interface is created on Host with local static IP e.g. 192.168.1.10 and also emulator must be set with same subnet e.g. 192.168.1.11.
The limitation with this network mode is the emulator can be accessed only from local host machine. 


2-Bridge Mode with DHCP support: 
    Emulator to have it’s own IP and to access from outside then user need to setup a bridge.
The bridge must have two Ethernet interface one is tap interface for emulator and other one is physical Ethernet interface to communicate outside 
and fetch IP from DHCP sever for emulator. 


In case emulator failed to get the IP address from DHCP server then it will consider the IP address from configuration file.
The script provides option to save IP address in configuration file. 


Warning: If the host machine is logged in through remote session like SSH, VNC etc., may lose 
connection for few seconds until bridge gets an IP from DHCP server.  




3-Bridge mode without DHCP support: 
    It is same as above network mode, except user have to provide IP address manually for bridge and emulator. 
This network is recommended only when DHCP server is not available in user network. 


Warning: If the host machine is logged in through remote session like SSH, VNC etc., 
it will lose the connection. So it is recommended to run the script directly on the host machine. 


4-Remove Tap network : This option to remove the tap network. 


5-Remove Bridge network: To bring back the attached physical Ethernet interface to normal functionality , use this option.


6-Show/edit emulator IP configuration from configuration file : User can configure/view Emulator IP from/in configuration file.


7-Help: Shows help message to user


8- Exit - Exits script 


                                                                                                                                                                                            " 
}


while true; do
    echo "Select network mode for emulator"
    echo "1-Tap network"
    echo "2-Bridge network with DHCP support"
    echo "3-Bridge network without DHCP support"
    echo "4-Remove Tap network"
    echo "5-Remove Bridge network"
    echo "6-Show/edit emulator IP configuration from configuration file"
    echo "7-Help"
    echo "8-Exit"
    read -p "Enter value [1-8]:" yn
    case $yn in
            [1] ) tap_interface_support
            break;;
        [2] ) echo "Warning: If the host machine is logged in through remote session like SSH, VNC etc.,may lose connection for few seconds until bridge gets an IP from DHCP server" 
            read -p "Proceed to create bridge network [y/n]" option
            if [ "$option" == "n" ] || [ "$option" == "N" ] || [ "$option" == "no" ] || [ "$option" == "NO" ]; then
               exit 1
            fi
            DHCP_Support_Enabled=1
            Dont_set_IP_for_tap=1
            DHCP_Support
            break;;
        [3] ) echo "Warning: If the host machine is logged in through remote session like SSH, VNC etc.,it will lose the connection. So it is recommended to run the script directly on the host machine"
            read -p "Proceed to create bridge network [y/n]" option
            if [ "$option" == "n" ] || [ "$option" == "N" ] || [ "$option" == "no" ] || [ "$option" == "NO" ]; then
               exit 1
            fi
            DHCP_Support_Enabled=0
            Dont_set_IP_for_tap=1
            DHCP_Support
            break;;
        [4] ) Remove_tap_network
            break;;
        [5] ) Remove_bridge_network
            break;;
        [6] ) get_ip_for_emulator
            break;;
        [7] ) show_help_content
            break;;
        [8] ) exit
            ;;
        * ) echo "Error - Enter value between 1 to 8";;
    
    esac
done

```

---

