---
title: "NoMachine NX Server not working Mepis 6.5"
date: 2007-06-29
forum: General Help
---

### Post by hexstar on 2007-06-29
Hello, I am trying to setup NoMachine NX server on my Mepis 6.5 install, I have another machine which I'm using to test the setup with. The servers IP is 192.168.8.204 and the client's IP is 192.168.8.208. The server appears to be setup fine and can be utilized fine with nxmanager locally, however when I try to connect to the server using the NX client on my test machine (also Mepis 6.5) it gets to the starting X session bit and then the connection oddly fails.... Here's what the NX Client has to say about this:

NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.

Info: Proxy running in client mode with pid '12409'.
Session: Starting session at 'Thu Jun 28 18:07:40 2007'.
Info: Connecting to remote host '192.168.8.204:5007'.
Info: Connection to remote proxy '192.168.8.204:5007' established.
Warning: Connected to remote NXPROXY version 3.0.0 with local version 2.1.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4194304/8192KB/8192KB.
Info: Using image streaming parameters 50/128/1024KB/2048/256.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-jpeg-7' with session 'unix-kde'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Using ZLIB data compression 1/1/0.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Using remote server '192.168.8.204:5007'.
Info: Listening for font server connections on port '11007'.
Session: Session started at 'Thu Jun 28 18:07:40 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
Session: Session terminated at 'Thu Jun 28 18:07:45 2007'.
Warning: Parent process appears to be dead. Exiting keeper.

and here's what the server says:

Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: initialization: starting parse of config file '/usr/NX/etc/node.cfg' Logger::log nxserver 1072
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: disabling logging for package 'NXMsg' 'Logger::disablePackage'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: disabling logging for package 'NXLogin' 'Logger::disablePackage'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: disabling logging for package 'InfoManager' 'Logger::disablePackage'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: WARNING: Load balancing is not permitted on this server. 'main::chk_license'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: WARNING: Please check the terms and conditions of your subscription. 'main::chk_license'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: handling command 'welcome' '' 'NXShell::handle_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received command 'hello' 'NXCLIENT - Version 3.0.0' 'NXShell::get_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: handling command 'hello' 'NXCLIENT - Version 3.0.0' 'NXShell::handle_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received command 'set' 'SHELL_MODE SHELL' 'NXShell::get_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: handling command 'set' 'SHELL_MODE SHELL' 'NXShell::handle_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received command 'set' 'AUTH_MODE PASSWORD' 'NXShell::get_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: handling command 'set' 'AUTH_MODE PASSWORD' 'NXShell::handle_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received command 'login' '' 'NXShell::get_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: handling command 'login' '' 'NXShell::handle_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Local IP determined from SSH_CONNECTION: 192.168.8.208 1456 192.168.8.204 22 'NXClientConnection::getLocalIp'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locking file /usr/NX/etc/guests.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3141
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3152
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocked 'main::unLockFile'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: redirecting stderr to file '/dev/null' '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run_command: stdin will be not redirect '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run_command: stdout will be not redirect '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: trying to run command 'stty -echo' '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals are now blocked ... Logger::log nxserver 2397
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5575]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: closed STDERR redirected file '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: command is running with pid: 5575 '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: command STDIN will be not closed '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: not added command STDOUT to list of selector set: pipe was not created '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: not added command STDERR to list of selector set: redirected to a file '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5575' finished with: 1 '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5575' stdout was '' 'main::run_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5575' stderr was '' 'main::run_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: redirecting stderr to file '/dev/null' '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run_command: stdin will be not redirect '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run_command: stdout will be not redirect '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: trying to run command 'stty echo' '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals are now blocked ... Logger::log nxserver 2397
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5576]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: closed STDERR redirected file '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: command is running with pid: 5576 '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: command STDIN will be not closed '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: not added command STDOUT to list of selector set: pipe was not created '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: not added command STDERR to list of selector set: redirected to a file '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5576' finished with: 1 '(eval)'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5576' stdout was '' 'main::run_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5576' stderr was '' 'main::run_command'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: user login is hex (NXShell). Stored status. 'Logger::statusPush'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: user password is '******' (NXShell). Stored status. 'Logger::statusPush'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: using 'sshd authentication' (NXShell). Stored status. 'Logger::statusPush'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: checking user 'hex@127.0.0.1:22' credentials 'NXNssUserManager::auth'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: executing command: '/usr/NX/bin/nxssh -nxauthonly -o 'StrictHostKeyChecking no' -l hex 127.0.0.1 -p 22 -2' 'NXNssUserManager::auth'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: nxssh pid is: 5577 'NXNssUserManager::auth'
Jun 29 09:52:37 localhost NXSERVER-3.0.0-61[5570]: DEBUG: printing password to nxssh stdin: ******* '(eval)'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received data in stdout channel: 'NX> 205 Password: ' '(eval)'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received data in stdout channel: '\n' '(eval)'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received data in stdout channel: 'NX> 206 ssh-userauth2 successful: method keyboard-interactive\n' '(eval)'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: stdout channel was closed '(eval)'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: stderr was closed '(eval)'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: waiting process: with pid '5577' 'WaitProcess::waitProcess'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: waiting process: using 5s as timeout 'WaitProcess::waitProcess'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: process with pid '5577' has exited 'WaitProcess::waitProcess'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: process exit status is '0' 'WaitProcess::getExitStatus'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: User 'hex' logged in from '192.168.8.208'. 'NXLogin::set'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locking file /usr/NX/etc/users.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3141
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3152
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocked 'main::unLockFile'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received command 'listsession' '--user="hex" --status="suspended,running" --geometry="1024x768x16+render" --type="unix-kde"' 'NXShell::get_command'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: handling command 'listsession' '--user="hex" --status="suspended,running" --geometry="1024x768x16+render" --type="unix-kde"' 'NXShell::handle_command'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getLastParameters: command parameters '--user="hex" --status="suspended,running" --geometry="1024x768x16+render" --type="unix-kde"'. NXShell::getLastParameters handlers/nxserver 4226
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter string is '--user="hex" --status="suspended,running" --geometry="1024x768x16+render" --type="unix-kde"'. 'NXShell::getParameters'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--user=hex'. 'NXShell::getParameters'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--status=suspended,running'. 'NXShell::getParameters'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--geometry=1024x768x16+render'. 'NXShell::getParameters'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--type=unix-kde'. 'NXShell::getParameters'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: command parameters '--user="hex" --status="suspended,running" --geometry="1024x768x16+render" --type="unix-kde"' 'NXShell::getParameters'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3141
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3152
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocked 'main::unLockFile'
Jun 29 09:52:38 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received command 'startsession' '--link="adsl" --backingstore="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="test" --type="unix-kde" --geometry="1024x721" --client="linux" --keyboard="pc105/us" --screeninfo="1024x721x16+render"' 'NXShell::get_command'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: handling command 'startsession' '--link="adsl" --backingstore="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="test" --type="unix-kde" --geometry="1024x721" --client="linux" --keyboard="pc105/us" --screeninfo="1024x721x16+render"' 'NXShell::handle_command'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getLastParameters: command parameters '--link="adsl" --backingstore="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="test" --type="unix-kde" --geometry="1024x721" --client="linux" --keyboard="pc105/us" --screeninfo="1024x721x16+render"'. NXShell::getLastParameters handlers/nxserver 1990
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter string is '--link="adsl" --backingstore="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="test" --type="unix-kde" --geometry="1024x721" --client="linux" --keyboard="pc105/us" --screeninfo="1024x721x16+render"'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--link=adsl'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--backingstore=1'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--cache=8M'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--images=32M'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--shmem=1'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--shpix=1'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--strict=0'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--composite=1'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--media=0'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--session=test'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--type=unix-kde'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--geometry=1024x721'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: NX client operating system is linux. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--client=linux'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--keyboard=pc105/us'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: getParameters: parameter '--screeninfo=1024x721x16+render'. 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: command parameters '--link="adsl" --backingstore="1" --cache="8M" --images="32M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="test" --type="unix-kde" --geometry="1024x721" --client="linux" --keyboard="pc105/us" --screeninfo="1024x721x16+render"' 'NXShell::getParameters'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3141
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3152
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocked 'main::unLockFile'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: User profiles are disabled. Skipping check of item: server-clipboard into profiles 'NXProfilesManager::check_item_permission'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3141
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3152
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocked 'main::unLockFile'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: User profiles are disabled. Skipping check of item: client-clipboard into profiles 'NXProfilesManager::check_item_permission'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Enabling persistent sessions for all users 'NXShell::handler_session_start'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Searching a session to reconnect... 'NXShell::Static'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: No session to reconnect found 'NXShell::Static'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Enable load balancing: 1 'main::selectNode'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Available host list: localhost:22 'main::selectNode'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Selected node host no: 1 of: 1 available host 'main::selectNode'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Configured node host list: localhost:22 'main::selectNode'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3141
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locked. Immediately flock file. fileno: 4 'main::lockFile'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocking file... fileno: 4 main::unLockFile nxserver 3152
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocked 'main::unLockFile'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: User profiles are disabled. Skipping check of item: localhost/22 into profiles 'NXProfilesManager::check_item_permission'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Checking host: localhost for user:hex (checking response:localhost) 'main::selectNode'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: Selected node host:localhost with port:22 'main::selectNode'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Checking running nodes: localhost:22 'main::checkNodeIsEnabledDisabled'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Found nodes: localhost:22 in status: running 'main::checkNodeIsEnabledDisabled'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: Current selected node: localhost is in status: running 'main::selectNode'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: user's sessions are: 0 'NXSession2::Static'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: local sessions has: 'NXSession2::Static'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: searching for next display to use from num. '1000', to num. '1199' 'NXSession2::Static'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: last used display num. is '1010' 'NXSession2::Static'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: search will stop to display num. '1010' 'NXSession2::Static'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: checking resources of display num. '1011' 'NXSession2::Static'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: selected user 'hex' is authenticated (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: password for selected user is in 'text' mode (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: preferred auth method is '' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: selected NX Node with host name 'localhost', port '22' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: selected publickey method to login NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l hex localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals are now blocked ... Logger::log nxserver 2397
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5599]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: nxssh child pid is: 5599 (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:40 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: added pid 5599 to the child set. Now pids to wait are: 5599 'main::__add_process_to_wait'
Jun 29 09:52:43 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received data in out channel from NX Node: 'NX> 1000 NXNODE - Version 3.0.0-71 \n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:43 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received message 'CONNECTED' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:43 localhost NXSERVER-3.0.0-61[5570]: DEBUG: sent request for service 'chkDisplay' to NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:43 localhost NXSERVER-3.0.0-61[5570]: DEBUG: sent parameters 'display=1011&to_display=1199' to NX Node (NXNodeExec). Stored status. 'Logger::statusPush'



Please help, what's wrong? How do I fix this? Thanks! :)

---

### Post by hexstar on 2007-06-29
server output continued...

Jun 29 09:52:43 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received data in out channel from NX Node: 'NX> 151 1011\nNX> 1001 Bye.\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:44 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received message 'BYE' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:44 localhost NXSERVER-3.0.0-61[5570]: DEBUG: NX Node err channel was closed (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:44 localhost NXSERVER-3.0.0-61[5570]: DEBUG: closing nxssh's in, out, err FDs (flagfinished is: 1) (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: waiting process: with pid '5599' 'WaitProcess::waitProcess'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: waiting process: using 5s as timeout 'WaitProcess::waitProcess'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: process with pid '5599' has exited 'WaitProcess::waitProcess'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: process exit status is '0' 'WaitProcess::getExitStatus'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: process exit status is '0' 'WaitProcess::getExitStatus'

---

### Post by hexstar on 2007-06-29
and....

Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: nxssh process exited with '0' 'NXNodeExec::exec'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: connection to NX Node finished correctly (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3141
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locked. Immediately flock file. fileno: 4 'main::lockFile'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocking file... fileno: 4 main::unLockFile nxserver 3152
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocked 'main::unLockFile'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: User profiles are disabled. Skipping check of item: unix-kde into profiles 'NXProfilesManager::check_item_permission'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: Selected session type: unix-kde allowed in the profile of user: hex 'NXShell::Static'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: trying to run command 'ps -e' '(eval)'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals are now blocked ... Logger::log nxserver 2397
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5662]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: command is running with pid: 5662 '(eval)'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: closed command STDIN '(eval)'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: added command STDOUT to list of selector set '(eval)'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: added command STDERR to selector set '(eval)'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5662' stderr was closed. '(eval)'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5662' stdout was closed. '(eval)'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5662' finished with: 0 '(eval)'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5662' stdout was ' PID TTY TIME CMD\n 1 ? 00:00:00 init\n 2 ? 00:00:00 ksoftirqd/0\n 3 ? 00:00:00 watchdog/0\n 4 ? 00:00:00 events/0\n 5 ? 00:00:00 khelper\n 6 ? 00:00:00 kthread\n 8 ? 00:00:00 kblockd/0\n 9 ? 00:00:00 kacpid\n 81 ? 00:00:00 khubd\n 135 ? 00:00:00 pdflush\n 136 ? 00:00:00 pdflush\n 138 ? 00:00:00 aio/0\n 137 ? 00:00:00 kswapd0\n 139 ? 00:00:00 jfsIO\n 140 ? 00:00:00 jfsCommit\n 141 ? 00:00:00 jfsSync\n 730 ? 00:00:00 kseriod\n 853 ? 00:00:00 ata/0\n 854 ? 00:00:00 ata_hotplug/0\n 872 ? 00:00:00 khpsbpkt\n 883 ? 00:00:00 reiserfs/0\n 1156 ? 00:00:00 udevd\n 1936 ? 00:00:00 shpchpd_event\n 2010 ? 00:00:00 kgameportd\n 2337 ? 00:00:00 dhclient3\n 2523 ? 00:00:00 wrap_wq\n 2524 ? 00:00:00
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: process '5662' stderr was '' 'main::run_command'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: inserting session sessionId:CCABE0FE17B390E9312D4F242158B61B on 'running' DB 'NXSession2::insertSession'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Node is on localhost, connection will be unencrypted 'main::checkNodeMode'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Proxy IP: $balance_host:localhost 'NXShell::handler_session_start'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Proxy IP: should be $balance_host:192.168.8.204 'NXShell::handler_session_start'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3141
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3152
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Unlocked 'main::unLockFile'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1005 'NXNodeExec:nMessage'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1006 'NXNodeExec:nMessage'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1008 'NXNodeExec:nMessage'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1009 'NXNodeExec:nMessage'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1010 'NXNodeExec:nMessage'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: selected user 'hex' is authenticated (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: password for selected user is in 'text' mode (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: preferred auth method is '' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: selected NX Node with host name 'localhost', port '22' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: selected publickey method to login NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l hex localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals are now blocked ... Logger::log nxserver 2397
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5663]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: nxssh child pid is: 5663 (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:46 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: added pid 5663 to the child set. Now pids to wait are: 5599 5663 'main::__add_process_to_wait'
Jun 29 09:52:48 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received data in out channel from NX Node: 'NX> 1000 NXNODE - Version 3.0.0-71 \n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:48 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received message 'CONNECTED' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:48 localhost NXSERVER-3.0.0-61[5570]: DEBUG: sent request for service 'startsession' to NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:48 localhost NXSERVER-3.0.0-61[5570]: DEBUG: sent parameters 'user=hex&userip=192%2e168%2e8%2e208&uniqueid=CCABE0FE17B390E9312D4F242158B61B&display=1011&license= %28None%29&subscriptionid=None&productid=LFE&reconnect=1&balance_host=localhost&balance_host_realip= 192%2e168%2e8%2e204&encryption_mode=1&connection=local&images=32M&cache=8M&client=linux&media=0&back ingstore=1&strict=0&clipboard=both&shpix=1&rootless=0&composite=1&session=test&shmem=1&type=unix%2dk de&virtualdesktop=1&screeninfo=1024x721x16%2brender&keyboard=pc105%2fus&geometry=1024x721&link=adsl' to NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received data in out channel from NX Node: 'NX> 700 Session id: eds_linux_box-1011-CCABE0FE17B390E9312D4F242158B61B\nNX> 705 Session display: 1011\nNX> 703 Session type: unix-kde\nNX> 701 Proxy cookie: 0BCF7113622EB58C3039B5CA8885C8D8\nNX> 702 Proxy IP: 192.168.8.204\nNX> 706 Agent cookie: 0BCF7113622EB58C3039B5CA8885C8D8\nNX> 704 Session cache: unix-kde\nNX> 707 SSL tunneling: 0\nNX> 708 Subscription: LFE/None/LFEN/None\nNX> 710 Session status: running\nNX> 1007 Commit and close FH\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received message 'COMMIT2' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: cleared child set 'main::__reset_process_to_wait'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: waiting for message 'BYE' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Calling handler function: 'NXUtmp::add' for 'connected to nxnode' event 'NXNodeExec::__onMessageRun'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: NXUtmp:1011,192.168.8.208,hex 'NXUtmp::add'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: trying to run command '/usr/NX/bin/nxuexec nxwtmpadd.sh 1011 192.168.8.208 hex' '(eval)'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Signals are now blocked ... Logger::log nxserver 2397
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: DEBUG: returning to interactive mode (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: Session 'CCABE0FE17B390E9312D4F242158B61B' started by user 'hex'. 'NXShell::handler_session_start'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: DEBUG: Server pid for session 'CCABE0FE17B390E9312D4F242158B61B' is: 5780 'NXShell::handler_session_start'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: ERROR: run command: no child process with pid 5599 Logger::log nxserver 3059
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: DEBUG: run command: deleted pid 5599 from the set. Now pids to wait are: 5663 'main::__run_command_waitpid'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: DEBUG: received command 'bye' '' 'NXShell::get_command'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: DEBUG: handling command 'bye' '' 'NXShell::handle_command'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5570]: User 'hex' from '192.168.8.208' logged out. 'NXLogin::reset'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: command is running with pid: 5781 '(eval)'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: closed command STDIN '(eval)'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: added command STDOUT to list of selector set '(eval)'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: added command STDERR to selector set '(eval)'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5781]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5781' stdout was closed. '(eval)'
Jun 29 09:52:52 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5781' stderr was closed. '(eval)'
Jun 29 09:52:53 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5781' finished with: 0 '(eval)'
Jun 29 09:52:53 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5781' stdout was '' 'main::run_command'
Jun 29 09:52:53 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5781' stderr was '' 'main::run_command'
Jun 29 09:52:53 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Handler function finished 'NXNodeExec::__onMessageRun'
Jun 29 09:52:54 localhost NXNODE-3.0.0-71[5669]: Using port '1011' on node 'eds_linux_box' for session 'unix-kde'. Logger::log nxnode 5750
Jun 29 09:52:54 localhost NXNODE-3.0.0-71[5669]: Using host from available host list: 'localhost'. Logger::log nxnode 5751
Jun 29 09:52:54 localhost NXNODE-3.0.0-71[5821]: ERROR: Error when monitoring session: Could not open default font 'fixed' 'NXSessionMonitor::__setSessionStatus'
Jun 29 09:52:54 localhost NXNODE-3.0.0-71[5821]: NXSessionMonitor: killing unexpected agent running with pid '5776' with signal '15' 'NXSessionMonitor::monitorStatus'
Jun 29 09:52:54 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Recived request for a run nxmonitor: '(eval)'
Jun 29 09:52:54 localhost NXSERVER-3.0.0-61[5780]: DEBUG: No registered handler function for message: '' 'NXNodeExec::__onMessageRun'
Jun 29 09:52:54 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in out channel from NX Node: '\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:54 localhost NXSERVER-3.0.0-61[5780]: DEBUG: No registered handler function for message: '1015' 'NXNodeExec::__onMessageRun'
Jun 29 09:52:57 localhost NXNODE-3.0.0-71[5821]: NXSessionMonitor: killing unexpected agent running with pid '5776' with signal '15' 'NXSessionMonitor::monitorStatus'
Jun 29 09:52:58 localhost NXNODE-3.0.0-71[5821]: NXSessionMonitor: killing unexpected agent running with pid '5776' with signal '9' 'NXSessionMonitor::monitorStatus'
Jun 29 09:52:58 localhost NXNODE-3.0.0-71[5669]: ERROR: Unexpected termination of nxagent because of signal: 9 Logger::log nxnode 3752
Jun 29 09:52:58 localhost NXNODE-3.0.0-71[5669]: ERROR: run command: process: 5776 died because of signal: 9 Logger::log nxnode 3759
Jun 29 09:52:58 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in out channel from NX Node: 'Unexpected termination of nxagent because of signal: 9\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:58 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Removing not recognized buffer from stdout:[Unexpected termination of nxagent because of signal: 9\n] (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:58 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in err channel from NX Node: 'Unexpected termination of nxagent because of signal: 9\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:00 localhost NXNODE-3.0.0-71[5821]: Directory '/home/hex/.nx/C-eds_linux_box-1011-CCABE0FE17B390E9312D4F242158B61B' renamed into '/home/hex/.nx/F-C-eds_linux_box-1011-CCABE0FE17B390E9312D4F242158B61B' for further investigation Logger::log nxnode 5945
Jun 29 09:53:00 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in out channel from NX Node: 'NX> 1004 Error: \n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:00 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Error: received message 'ERROR' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:00 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in err channel from NX Node: 'Session monitor for session id 'eds_linux_box-1011-CCABE0FE17B390E9312D4F242158B61B' finished with errors:\nNXSessionMonitor::error at NXSessionMonitor.pm line 1381, <STDIN> line 2.\nCould not open default font 'fixed'\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:00 localhost NXSERVER-3.0.0-61[5780]: DEBUG: closing nxssh's in, out, err FDs (flagfinished is: 1) (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:01 localhost NXNODE-3.0.0-71[5669]: Session 'unix-kde' on port '1011' failed. Logger::log nxnode 6029
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: waiting process: with pid '5663' 'WaitProcess::waitProcess'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: waiting process: using 5s as timeout 'WaitProcess::waitProcess'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: no process with pid: '5663' to wait 'WaitProcess::waitProcess'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: NXNodeExec: nxssh not finish but change parent id 'NXNodeExec::exec'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: NXNodeExec: For avoid zombie proces killing nxssh process '5663' with signal '9' 'NXNodeExec::exec'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: ERROR: NXNodeExec: Cannot kill nxssh process: No such process 'NXNodeExec::exec'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Calling handler function: 'NXUtmp::remove' for 'disconnected from node' event 'NXNodeExec::__onMessageRun'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: trying to run command '/usr/NX/bin/nxuexec nxwtmpdel.sh 1011 192.168.8.208 hex' '(eval)'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Signals are now blocked ... Logger::log nxserver 2397
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: command is running with pid: 5884 '(eval)'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5884]: DEBUG: Signals unblocked Logger::log nxserver 2419
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: closed command STDIN '(eval)'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: added command STDOUT to list of selector set '(eval)'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: added command STDERR to selector set '(eval)'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5884' stdout was closed. '(eval)'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5884' stderr was closed. '(eval)'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5884' finished with: 0 '(eval)'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5884' stdout was '' 'main::run_command'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: run command: process '5884' stderr was '' 'main::run_command'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Handler function finished 'NXNodeExec::__onMessageRun'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Error: NX Node finished with errors (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: session sessionId:CCABE0FE17B390E9312D4F242158B61B failed 'NXShell::Static'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: back from close [2592000] 'NXShell::Static'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Going to remove session from session dbCCABE0FE17B390E9312D4F242158B61B 'NXShell::Static'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: DEBUG: handling command 'exit' '' 'NXShell::handle_command'
Jun 29 09:53:02 localhost NXSERVER-3.0.0-61[5780]: User 'hex' from '192.168.8.208' logged out. 'NXLogin::reset'

---

### Post by hexstar on 2007-06-29
the most critical part in that log btw seems to be...

Jun 29 09:52:54 localhost NXNODE-3.0.0-71[5821]: ERROR: Error when monitoring session: Could not open default font 'fixed' 'NXSessionMonitor::__setSessionStatus'
Jun 29 09:52:54 localhost NXNODE-3.0.0-71[5821]: NXSessionMonitor: killing unexpected agent running with pid '5776' with signal '15' 'NXSessionMonitor::monitorStatus'
Jun 29 09:52:54 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Recived request for a run nxmonitor: '(eval)'
Jun 29 09:52:54 localhost NXSERVER-3.0.0-61[5780]: DEBUG: No registered handler function for message: '' 'NXNodeExec::__onMessageRun'
Jun 29 09:52:54 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in out channel from NX Node: '\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:54 localhost NXSERVER-3.0.0-61[5780]: DEBUG: No registered handler function for message: '1015' 'NXNodeExec::__onMessageRun'
Jun 29 09:52:57 localhost NXNODE-3.0.0-71[5821]: NXSessionMonitor: killing unexpected agent running with pid '5776' with signal '15' 'NXSessionMonitor::monitorStatus'
Jun 29 09:52:58 localhost NXNODE-3.0.0-71[5821]: NXSessionMonitor: killing unexpected agent running with pid '5776' with signal '9' 'NXSessionMonitor::monitorStatus'
Jun 29 09:52:58 localhost NXNODE-3.0.0-71[5669]: ERROR: Unexpected termination of nxagent because of signal: 9 Logger::log nxnode 3752
Jun 29 09:52:58 localhost NXNODE-3.0.0-71[5669]: ERROR: run command: process: 5776 died because of signal: 9 Logger::log nxnode 3759
Jun 29 09:52:58 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in out channel from NX Node: 'Unexpected termination of nxagent because of signal: 9\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:58 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Removing not recognized buffer from stdout:[Unexpected termination of nxagent because of signal: 9\n] (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:52:58 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in err channel from NX Node: 'Unexpected termination of nxagent because of signal: 9\n' (NXNodeExec). Stored status. 'Logger::statusPush'

and...

Jun 29 09:53:00 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in out channel from NX Node: 'NX> 1004 Error: \n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:00 localhost NXSERVER-3.0.0-61[5780]: DEBUG: Error: received message 'ERROR' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:00 localhost NXSERVER-3.0.0-61[5780]: DEBUG: received data in err channel from NX Node: 'Session monitor for session id 'eds_linux_box-1011-CCABE0FE17B390E9312D4F242158B61B' finished with errors:\nNXSessionMonitor::error at NXSessionMonitor.pm line 1381, <STDIN> line 2.\nCould not open default font 'fixed'\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:00 localhost NXSERVER-3.0.0-61[5780]: DEBUG: closing nxssh's in, out, err FDs (flagfinished is: 1) (NXNodeExec). Stored status. 'Logger::statusPush'
Jun 29 09:53:01 localhost NXNODE-3.0.0-71[5669]: Session 'unix-kde' on port '1011' failed. Logger::log nxnode 6029

and yes, I have updated the NX client on the test machine and tried the following fix on the server to no avail: [http://www.mepis.org/docs/en/index.php/NX](http://www.mepis.org/docs/en/index.php/NX)

Any ideas? Thanks! :)

P.S. I'm posting this here because the mepis forum is not very active and since this forum is active and since mepis is based off of ubuntu people here should be able to provide me with support :)

---

### Post by hexstar on 2007-06-29
***bump***

---

### Post by bodhi.zazen on 2007-06-29
A few pointers :

1. This is Ubuntu, you may have better luck on the Mepis or NoMachine Forums. Mepis is sufficienlty different I would start there.

2. For long files like that, please use attachments (as text files).

3. We are all volunteers here and bumping you won thread after 5 hours is considered gauche.

We have an unanswered team and bumping your own thread makes if difficult or impossible for them to identify you as needing assistance.

---

### Post by paul382 on 2008-07-24
Hi to all,

It seems that there is some missing system files which causes these source codes and error codes. To recover theses files, you can use stellar phoenix [linux recovery]("http://www.data-recovery-linux.com") utility so that you didn't face this problem in near future. Check your files with the help of demo version of this software.

Thanks

---

