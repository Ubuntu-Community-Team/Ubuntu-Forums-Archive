---
title: "Error while running tcl file in ubuntu 12.04 LTS"
date: 2013-11-12
forum: General Help
---

### Post by mulyead on 2013-11-12
Hello,

I am using ns2.34 for my project purpose. I installed NS2.34 on ubuntu and also able to install ns-BGP on it. While running a tcl script i am getting following error.

   @ubuntu1204s:~/ns-allinone-2.34/ns-2.34/tcl/bgp/test$ ns drop-peer2.tcl 
  
 DROP-PEER2 Validation Test: 
  
  Three ASes connected in a line, each with one router. 
    AS 1       AS 0       AS 2 
    n1 }------{ n0 }------{ n2 
  
  
     (_o10 cmd line 1) 
     invoked from within 
 "_o10 cmd get-bgp-agent" 
     invoked from within 
 "catch "$self cmd $args" ret" 
     invoked from within 
 "if [catch "$self cmd $args" ret] { 
 set cls [$self info class] 
 global errorInfo 
 set savedInfo $errorInfo 
 error "error when calling class $cls: $args" $..." 
     (procedure "_o10" line 2) 
     (SplitObject unknown line 2) 
     invoked from within 
 "$n0 get-bgp-agent" 
     invoked from within 
 "set bgp_agent0 [$n0 get-bgp-agent]" 
     (file "drop-peer2.tcl" line 27) 

Please help me with the solution of the same.

Thanks in advance

---

