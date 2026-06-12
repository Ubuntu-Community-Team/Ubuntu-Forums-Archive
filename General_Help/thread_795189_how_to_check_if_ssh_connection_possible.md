---
title: "how to check if ssh connection possible?"
date: 2008-05-15
forum: General Help
---

### Post by starkes on 2008-05-15
Hey there

I'm trying to write a script to find out which machines on my network are linux ubuntu machines. it's a corporate network i guess, but small and on one subnet.

we have a portion of the network where new machines are given IP's, and another area reserved for statically assigned IP's. as we add new machines, they are given an IP within the dynamically assigned range initially, and I want to make a script to find out which machines in the dynamic range can be connected to with ssh so i can then extract some info and have them added to the static range.

I have a script that goes as far as checking if they can be pinged, but afterwards I would like it to check if there is an ssh server running, as this will narrow it down and let me know if im connecting to a windows machine or a linux machine (we add both periodically).

i can then use ssh to get the mac address and other information i need to have the computer's IP moved into the static range, but that i can figure out.

can anyone tell me if theres a way to use ssh and have it return whether or not it could initially connect, without just knowing this by trying to connect and seeing a prompt show up or not? or.. could i have a shell script check for that itself?



this is the script i'm currently using to check which of the static machines are pingable. I'd like to modify this possibly by one line only or so to have it check via ssh instead of just pining, because you can ping a windows machine too. None of our windows machines will accept an ssh connection off the bat, though. this works by hostname, not ip, though. replacing the first part of the hostname with xxx.xxx.xxx. is basically all i had to do to make it connect via ip, though, if that helps look at it more easily.


```
#!/bin/sh

if [ "$#" -lt 2 ] ; then
  clear
  echo "----------------------------------"
  echo "----------------------------------"
  echo " "
  echo "IMPROPER SYNTAX FOR THIS SCRIPT!"
  echo " "
  echo "USAGE: push_file.script filename number_start number_end"
  echo " "
  echo "----------------------------------"
  echo "----------------------------------"
  exit 1
fi

counter="$1"
max="$2"
finalstring=""
pathone="oa-j114g-0"
pathtwo="oa-j114g-"

step=1


while [ $counter -le $max ] ; do

  if [ $counter -le 9 ]
  then
	finalstring="$pathone$counter"
  else
	finalstring="$pathtwo$counter"
  fi
  COUNT=1
  echo "Connecting to $finalstring..."
  pingcount=$(ping -c $COUNT $finalstring | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $pingcount -eq 0 ]; then
    echo "$finalstring is down (ping failed) at $(date)"
    echo $finalstring >> inactive_hosts.txt
  else
    echo "$finalstring found"
    echo $finalstring >> active_hosts.txt
  fi
  counter=$( expr $counter + $step )
done
exit 0
```

any help would be great.

thanks,
cory.

---

### Post by antwerx on 2008-05-15
I am not sure about the scripting aspect of what you are doing but I would turn to Nmap.  Nmap should be able to tell you all that you are looking for.  I would also think you should be able to script the Nmap scans.

Hope this helps some.

---

### Post by Mr A Mouse on 2008-05-15
Check to see if port 22 is open on the computers that you're checking--port 22 is the default ssh port.

---

### Post by starkes on 2008-05-15
after checking out nmap, it seems im going to be about where i started. I cant find a way to get it to return say, a 0 or a 1, which i can easily check in a shell script. 

it spits a whole lot of information depending on how you use it and i havent found a minimal enough set of information that i can easily check it.

---

### Post by talz13 on 2008-05-15
> **starkes said:**
> after checking out nmap, it seems im going to be about where i started. I cant find a way to get it to return say, a 0 or a 1, which i can easily check in a shell script. 

it spits a whole lot of information depending on how you use it and i havent found a minimal enough set of information that i can easily check it.

```
nmap -p 22 --open -oG nmapgrep.txt 192.168.1.0/24
```

That command spit out this file:
```
# Nmap 4.20 scan initiated Thu May 15 11:36:42 2008 as: nmap -p 22 --open -oG nmapgrep.txt 192.168.1.0/24
Host: 192.168.1.1 (router)      Status: Up
Host: 192.168.1.5 (server)      Ports: 22/open/tcp//ssh///
Host: 192.168.1.8 (brotherPrinter)      Status: Up
Host: 192.168.1.9 (jeff-laptop-wifi)    Status: Up
Host: 192.168.1.114 (JEFFLAPTOP)        Status: Up
Host: 192.168.1.143 (jeffvm)    Status: Up
# Nmap run completed at Thu May 15 11:36:49 2008 -- 256 IP addresses (6 hosts up) scanned in 7.239 seconds
```

Just cat the output file "nmapgrep.txt" or whatever you want to call it, pipe it to grep, and search for "open":
```
jeff@server:~$ cat nmapgrep.txt | grep open
# Nmap 4.20 scan initiated Thu May 15 11:36:42 2008 as: nmap -p 22 --open -oG nmapgrep.txt 192.168.1.0/24
Host: 192.168.1.5 (server)      Ports: 22/open/tcp//ssh///
jeff@server:~$
```

I got it to scan my network for open ssh ports, then a command to list all hosts that found ssh open like this.  You should easily be able to parse out the host line for the IP and do stuff with it.

---

### Post by starkes on 2008-05-15
oh boy, now this is something I can roll with. 

I bet this is about all I need.

Thanks!!

---

### Post by jimv on 2008-05-15
Maybe I'm missing something, but Linux machines don't have SSH servers enabled by default, do they?

---

### Post by antwerx on 2008-05-15
Thanks for this.  I knew there would be a way to do it.

---

### Post by Mr A Mouse on 2008-05-15
> **jimv said:**
> Maybe I'm missing something, but Linux machines don't have SSH servers enabled by default, do they?

Some distributions might, but in Ubuntu no--SSH is not installed or enabled in the default setup.

---

### Post by HermanAB on 2008-05-15
You can use telnet to debug TCP connections:

$ telnet serveripaddress 22

Cheers,

Herman

---

### Post by starkes on 2008-05-15
in my case, all the hard drives for the machines are just clones of one original drive, which had ssh installed and enabled and whatnot.

---

### Post by Monicker on 2008-05-15
> **jimv said:**
> Maybe I'm missing something, but Linux machines don't have SSH servers enabled by default, do they?

Several do.

Debian, Fedora/Redhat, Gentoo.  I'm sure there are others.

---

### Post by starkes on 2008-05-15
heres what i used to parse the file given by nmap so that it only shows the ip addresses found, not the rest of the information

cat nmapgrep.txt | grep -o '192\.168\.0\.[0-9][0-9][0-9]'

---

