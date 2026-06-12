---
title: "ssh login script"
date: 2013-03-05
forum: General Help
---

### Post by Rakeshvijayan on 2013-03-05
HI feed up with this topic of ssh login for taking backup automatically I got a expect script which will closed with out server's shell .please any one help me to correct this scrip > 
   
   
#!/usr/bin/expect
 set timeout 9 
set username [lindex $argv 0]
 set password [lindex $argv 1]
 set hostname [lindex $argv 2] 
log_user 0  
if {[llength $argv] == 0} 
{   send_user "Usage: scriptname username \'password\' hostname\n"   exit 1 }
  send_user "\n#####\n# $hostname\n#####\n"  
spawn ssh -q -o StrictHostKeyChecking=no $username@$hostname  
expect {   timeout { send_user "\nFailed to get password prompt\n"; exit 1 }
   eof { send_user "\nSSH failure for $hostname\n"; exit 1 }   "*assword" }  
send "$password\r"
  expect {   timeout { send_user "\nLogin failed. Password incorrect.\n"; exit 1}   "*\$ " }  
send_user "\nPassword is correct\n"
 send "exit\r"
 close





I  compiling this script it show that  passed is correct and I cant get into server terminal I need to  back up mysql file every day I usually use ""ssh  koha@ip and scp -r backup/ remoteuser@ipaddress:~/   ""

some times I forget to take whole this thats why I am again here with this topic , expecting a kind full help form  all masters that use this world 


Thanks

---

### Post by albandy on 2013-03-05
Are you using expect only for login purposes? Why don't you use your ssh public key for autologin?

---

### Post by prodigy_ on 2013-03-05
> **Rakeshvijayan said:**
> ```
set username [lindex $argv 0]
set password [lindex $argv 1]
set hostname [lindex $argv 2]
```
What's the point of scripting if you enter hostname and credentials manually anyway? You could as well use **ssh username@hostname** and type your password when prompted.

Or if you call expect from another script, you could use something much simpler like the following stock example from Wikipedia: ```
spawn ssh $user@machine
while {1} {
  expect {
 
    eof                          {break}
    "The authenticity of host"   {send "yes\r"}
    "password:"                  {send "$password\r"}
    "*\]"                        {send "exit\r"}
  }
}
wait
close $spawn_id
```

---

### Post by Rakeshvijayan on 2013-03-20
finaly I fedup this topic I cant able to make this one 


Thanks friends for the valuable time

---

