---
title: "Running expect on ubuntu"
date: 2014-08-21
forum: General Help
---

### Post by cbrun on 2014-08-21
I have an expect script that is not behaving and hope someone can see where I've gone astray.  I simply want to pick out the MAC address string from a response, as you can see, I get the line, but apparently it doesn't match my expect expression ... 

expect {
    "#" {
    send "show arp | inc  $ipaddr\r"
    }
     timeout {
    puts $errFile "LOGIN Failure for $SchID"
    }
}
expect {
    -re "\[0-9a-f]\[0-9a-f]\[0-9a-f]\[0-9a-f].\[0-9a-f]\[0-9a-f]\[0-9a-f]\[0-9a-f].\[0-9a-f]\[0-9a-f]\[0-9a-f]\[0-9a-f].\[0-9a-f]\[0-9a-f]\[0-9a-f]\[0-9a-f]" {
    set result $expect_out(0,string)
    puts "RESULT is $result"
   }
  timeout {
    send "quit\r"
   }

}


Here is the run:
cbrun@Linux-Net:~/scripts/findMAC$ ./MAClookupCisco 183 10.183.48.17


TVMS-3560#show arp | inc  10.183.48.17
Internet  10.183.48.17          136   00c0.ee9f.4255  ARPA   Vlan2

---

