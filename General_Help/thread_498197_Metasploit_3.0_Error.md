---
title: "Metasploit 3.0 Error"
date: 2007-07-11
forum: General Help
---

### Post by cnr437 on 2007-07-11
I tried to install Metasploit 3.0 and I installed everything that metasploit wants but it still doesn't work properly.

When I write "show exploits" it outputs these error messages >>

What should I do to solve that problem??

```
[-] Error while running command show: wrong constant name irix

Call stack:
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:1011:in `const_set'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:1011:in `mod_from_name'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:991:in `each'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:991:in `mod_from_name'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:848:in `load_module_from_file'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:725:in `demand_load_module'
/home/caner/Desktop/Hacking/framework-3.0/lib/rex/parser/ini.rb:144:in `each_with_index'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:722:in `each'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:722:in `each_with_index'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:722:in `demand_load_module'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:85:in `create'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:172:in `demand_load_modules'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:168:in `each_pair'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:168:in `demand_load_modules'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/core/module_manager.rb:118:in `each_module'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/ui/console/command_dispatcher/core.rb:1504:in `show_module_set'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/ui/console/command_dispatcher/core.rb:1380:in `show_exploits'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/ui/console/command_dispatcher/core.rb:864:in `cmd_show'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/ui/console/command_dispatcher/core.rb:850:in `each'
/home/caner/Desktop/Hacking/framework-3.0/lib/msf/ui/console/command_dispatcher/core.rb:850:in `cmd_show'
/home/caner/Desktop/Hacking/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:230:in `send'
/home/caner/Desktop/Hacking/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:230:in `run_command'
/home/caner/Desktop/Hacking/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:196:in `run_single'
/home/caner/Desktop/Hacking/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:191:in `each'
/home/caner/Desktop/Hacking/framework-3.0/lib/rex/ui/text/dispatcher_shell.rb:191:in `run_single'
/home/caner/Desktop/Hacking/framework-3.0/lib/rex/ui/text/shell.rb:120:in `run'
/home/caner/Desktop/Hacking/framework-3.0/msfconsole:77

```

---

