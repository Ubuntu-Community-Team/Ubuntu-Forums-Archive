---
title: "plymouth not firing up (logs included)"
date: 2013-01-15
forum: General Help
---

### Post by lepusfelix on 2013-01-15
For as long as I can remember, I have not had a graphical splash screen. I get a plain text 'Ubuntu 12.10' with four white pixels underneath that turn red (basically a plain text version of the graphical livecd splash). I include logs of plymouth-debug. Hopefully someone here can diagnose the problem better than I can.

```
[main.c]                                 check_logging:checking if console messages should be redirected and logged 
[main.c]                                 check_logging:logging will be enabled! 
[main.c]                        initialize_environment:source built on Aug 16 2012 
[main.c]                        initialize_environment:checking if '/dev/tty7' exists 
[main.c]                            check_for_consoles:checking for consoles 
[main.c]                        add_consoles_from_file:opening /sys/class/tty/console/active 
[main.c]                        add_consoles_from_file:reading file 
[main.c]                        add_consoles_from_file:couldn't read it: Success 
[main.c]                            check_for_consoles:falling back to kernel command line 
[main.c]                            check_for_consoles:After processing serial consoles there are now 0 text displays 
[main.c]                redirect_standard_io_to_device:redirecting stdio to /dev/tty7 
[main.c]                        initialize_environment:Making sure /run/plymouth exists 
[main.c]                        initialize_environment:initialized minimal work environment 
[main.c]                     attach_to_running_session:creating new terminal session 
[ply-terminal-session.c]                   ply_terminal_session_attach:ptmx not passed in, creating one 
[ply-terminal-session.c]                           open_pseudoterminal:opening device '/dev/ptmx' 
[ply-terminal-session.c]                           open_pseudoterminal: opened device '/dev/ptmx' 
[ply-terminal-session.c]                           open_pseudoterminal:creating pseudoterminal 
[ply-terminal-session.c]                           open_pseudoterminal:done creating pseudoterminal 
[ply-terminal-session.c]                           open_pseudoterminal:unlocking pseudoterminal 
[ply-terminal-session.c]                           open_pseudoterminal:unlocked pseudoterminal 
[ply-terminal-session.c]                   ply_terminal_session_attach:redirecting system console to terminal device 
[ply-terminal-session.c]                   ply_terminal_session_attach:done redirecting system console to terminal device 
[ply-terminal-session.c]            ply_terminal_session_start_logging:logging incoming console messages 
[main.c]                       get_cache_file_for_mode:returning cache file '/var/lib/plymouth//boot-duration' 
[main.c]                                          main:entering event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 347 (/bin/plymouth show-splash) with parent pid 344 (/bin/sh /scripts/init-top/plymouth) 
[ply-boot-server.c]                ply_boot_connection_on_request:got show splash request 
[main.c]      plymouth_should_ignore_show_splash_calls:checking if plymouth should be running 
[main.c]                            check_for_consoles:checking for consoles and adding displays 
[main.c]                        add_consoles_from_file:opening /sys/class/tty/console/active 
[main.c]                        add_consoles_from_file:reading file 
[main.c]                        add_consoles_from_file:couldn't read it: Socket operation on non-socket 
[main.c]                            check_for_consoles:falling back to kernel command line 
[main.c]                            check_for_consoles:After processing serial consoles there are now 0 text displays 
[main.c]             add_default_displays_and_keyboard:adding default displays and keyboard 
[ply-renderer.c]                      ply_renderer_open_plugin:trying to open renderer plugin /lib/plymouth/renderers/x11.so 
[ply-utils.c]                               ply_open_module:Could not load module "/lib/plymouth/renderers/x11.so": /lib/plymouth/renderers/x11.so: cannot open shared object file: No such file or directory
 
[ply-renderer.c]                      ply_renderer_open_plugin:trying to open renderer plugin /lib/plymouth/renderers/drm.so 
[./plugin.c]                                create_backend:creating renderer backend for device /dev/dri/card0 
[./plugin.c]                                   load_driver:Attempting to load driver '(null)' 
[./plugin.c]                                   load_driver:drmOpen failed 
[ply-renderer.c]                      ply_renderer_open_plugin:could not open rendering device for plugin /lib/plymouth/renderers/drm.so 
[ply-renderer.c]                      ply_renderer_open_plugin:trying to open renderer plugin /lib/plymouth/renderers/frame-buffer.so 
[./plugin.c]                                create_backend:creating renderer backend for device /dev/fb0 
[./plugin.c]                                   open_device:could not open '/dev/fb0': No such file or directory 
[ply-renderer.c]                      ply_renderer_open_plugin:could not open rendering device for plugin /lib/plymouth/renderers/frame-buffer.so 
[ply-renderer.c]                      ply_renderer_open_plugin:trying to open renderer plugin /lib/plymouth/renderers/vga16fb.so 
[./plugin.c]                                   open_device:could not open '/dev/fb0': No such file or directory 
[ply-renderer.c]                      ply_renderer_open_plugin:could not open rendering device for plugin /lib/plymouth/renderers/vga16fb.so 
[ply-renderer.c]                             ply_renderer_open:could not find suitable rendering plugin 
[main.c]             add_default_displays_and_keyboard:could not open renderer /dev/fb 
[main.c]             add_default_displays_and_keyboard:adding text display and keyboard for /dev/tty7 
[ply-terminal.c]                             ply_terminal_open:trying to open terminal '/dev/tty7' 
[ply-terminal.c]                 ply_terminal_look_up_geometry:looking up terminal text geometry 
[ply-terminal.c]                 ply_terminal_look_up_geometry:terminal is now 80x25 text cells 
[ply-terminal.c]                                 get_active_vt:Remembering that initial vt is 1 
[main.c]                                  set_keyboard:listening for keystrokes 
[main.c]                                  set_keyboard:listening for backspace 
[main.c]                                  set_keyboard:listening for enter 
[main.c]           plymouth_should_show_default_splash:checking if plymouth should show default splash 
[main.c]           plymouth_should_show_default_splash:using default splash because kernel command line has option "splash" 
[main.c]                           show_default_splash:Showing splash screen 
[main.c]                    find_system_default_splash:Trying to load /etc/plymouth//plymouthd.conf 
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /etc/plymouth//plymouthd.conf: No such file or directory 
[main.c]                    find_system_default_splash:failed to load /etc/plymouth//plymouthd.conf 
[main.c]              find_distribution_default_splash:Trying to load /lib/plymouth//plymouthd.defaults 
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /lib/plymouth//plymouthd.defaults: No such file or directory 
[main.c]              find_distribution_default_splash:failed to load /lib/plymouth//plymouthd.defaults 
[main.c]                           show_default_splash:Trying old scheme for default splash 
[main.c]                             start_boot_splash:Loading boot splash theme '/lib/plymouth/themes/default.plymouth' 
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /lib/plymouth/themes/default.plymouth: No such file or directory 
[ply-boot-splash.c]                          ply_boot_splash_free:freeing splash 
[ply-boot-splash.c]                               remove_displays:removing pixel displays 
[ply-boot-splash.c]                               remove_displays:removing text displays 
[main.c]                           show_default_splash:Could not start default splash screen,showing text splash screen 
[main.c]                             start_boot_splash:Loading boot splash theme '/lib/plymouth/themes/text.plymouth' 
[ply-key-file.c]                       ply_key_file_load_group:trying to load group Plymouth Theme 
[ply-key-file.c]                       ply_key_file_load_group:trying to load group ubuntu-text 
[ply-key-file.c]                      ply_key_file_load_groups:key file has no more groups 
[./plugin.c]                                 create_plugin:creating plugin 
[main.c]                             start_boot_splash:attaching plugin to event loop 
[main.c]                             start_boot_splash:attaching progress to plugin 
[main.c]      add_displays_and_keyboard_to_boot_splash:setting keyboard on boot splash 
[main.c]      add_displays_and_keyboard_to_boot_splash:adding text display on boot splash 
[ply-terminal.c]                             ply_terminal_open:terminal /dev/tty7 is already open 
[main.c]                             start_boot_splash:showing plugin 
[ply-boot-splash.c]                          ply_boot_splash_show:showing splash screen
 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 396 (/bin/plymouth update-root-fs --new-root-dir=/root) with parent pid 395 (/bin/sh /scripts/init-bottom/plymouth) 
[ply-boot-server.c]                ply_boot_connection_on_request:got newroot request 
[main.c]                                    on_newroot:new root mounted at "/root", switching to it 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1054 (/bin/plymouth update-root-fs --read-write) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got system initialized notification 
[main.c]                         on_system_initialized:system now initialized, opening log 
[main.c]                         get_log_file_for_mode:returning log file '/var/log/boot.log' 
[main.c]                               prepare_logging:opening log '/var/log/boot.log' 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1066 (/bin/plymouth --ping) with parent pid 1056 (/bin/sh -e /proc/self/fd/9) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 7 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1159 (plymouth --ping) with parent pid 1106 (/bin/sh /etc/rcS.d/S37apparmor start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1208 (plymouth --ping) with parent pid 1106 (/bin/sh /etc/rcS.d/S37apparmor start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'network-manager' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1214 (plymouth --ping) with parent pid 1106 (/bin/sh /etc/rcS.d/S37apparmor start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1236 (plymouth --ping) with parent pid 1230 (/bin/sh /etc/rcS.d/S47lm-sensors start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1240 (plymouth --ping) with parent pid 1230 (/bin/sh /etc/rcS.d/S47lm-sensors start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1246 (plymouth --ping) with parent pid 1230 (/bin/sh /etc/rcS.d/S47lm-sensors start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1256 (plymouth --ping) with parent pid 1250 (/bin/bash /etc/rcS.d/S50oss4-base start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1259 (plymouth --ping) with parent pid 1250 (/bin/bash /etc/rcS.d/S50oss4-base start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1265 (plymouth --ping) with parent pid 1250 (/bin/bash /etc/rcS.d/S50oss4-base start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'rc-sysinit' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'cups' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'rc' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty4' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty5' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'gdm' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'xinetd' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1342 (plymouth --ping) with parent pid 1337 (lightdm) 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'acpid' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tftpd-hpa' 
[./plugin.c]                                 update_status:status update 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'anacron' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty2' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1356 (plymouth --has-active-vt) with parent pid 1337 (lightdm) 
[ply-boot-server.c]                ply_boot_connection_on_request:got has_active vt? request 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty3' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'dmesg' 
[./plugin.c]                                 update_status:status update 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'tty6' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'whoopsie' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1360 (plymouth deactivate) with parent pid 1337 (lightdm) 
[ply-boot-server.c]                ply_boot_connection_on_request:got deactivate request 
[main.c]                                 on_deactivate:deactivating 
[main.c]                                 on_deactivate:deactivating keyboard 
[ply-boot-splash.c]                   ply_boot_splash_become_idle:telling splash to become idle 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'irqbalance' 
[./plugin.c]                                 update_status:status update 
[main.c]                           on_boot_splash_idle:boot splash idle 
[main.c]                           on_boot_splash_idle:deactivating splash 
[main.c]                   detach_from_running_session:detaching from terminal session 
[ply-terminal-session.c]                   ply_terminal_session_detach:stopping terminal logger 
[ply-terminal-session.c]             ply_terminal_session_stop_logging:stopping logging of incoming console messages 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 6 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 6 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:no more destinations remaing for fd 6, removing source 
[ply-terminal-session.c]                   ply_terminal_session_detach:unredirecting console messages 
[ply-terminal-session.c]                   ply_terminal_session_detach:ptmx wasn't originally passed in, destroying created one 
[main.c]                             deactivate_splash:deactivating terminal 
[ply-boot-server.c]            ply_boot_connection_on_deactivated:deactivated 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'plymouth-stop' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'hybrid-gfx' 
[./plugin.c]                                 update_status:status update 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'gdm' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'hybrid-gfx' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'lightdm' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'apport' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'cron' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'atd' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'anacron' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'dmesg' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'mountall-net' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'mountall-net' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'winbind' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'network-interface-security' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'network-interface' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'network-interface-security' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'network-interface' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1635 (plymouth --ping) with parent pid 1629 (/bin/sh /etc/rc2.d/S20hddtemp start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 6 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 6 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 6 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 6 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1685 (plymouth --ping) with parent pid 1629 (/bin/sh /etc/rc2.d/S20hddtemp start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 6 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 6 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 6 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 6 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1691 (plymouth --ping) with parent pid 1629 (/bin/sh /etc/rc2.d/S20hddtemp start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 6 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 6 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 6 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 6 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1736 (plymouth --ping) with parent pid 1730 (/bin/bash /etc/rc2.d/S99acpi-support start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 6 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 6 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 6 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 6 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'anacron' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1117 (plymouth-upstart-bridge) with parent pid 1 (/sbin/ini) 
[ply-boot-server.c]                ply_boot_connection_on_request:got update request 
[main.c]                                     on_update:updating status to 'anacron' 
[./plugin.c]                                 update_status:status update 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1837 (plymouth --ping) with parent pid 1730 (/bin/bash /etc/rc2.d/S99acpi-support start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 6 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 6 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 6 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 6 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1843 (plymouth --ping) with parent pid 1730 (/bin/bash /etc/rc2.d/S99acpi-support start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 6 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 6 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 6 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 6 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 6 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1873 (plymouth --ping) with parent pid 1862 (/bin/sh /etc/rc2.d/S99timidity start) 
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x405a30 for fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11 
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x405e50, 0x405a30) of fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11 
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop 
[ply-event-loop.c]             ply_event_loop_remove_source_node:failed to delete fd 11 from epoll watch list: Bad file descriptor 
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop 
[ply-boot-server.c]             print_connection_process_identity:connection is from pid 1870 (plymouth quit --retain-splash) with parent pid 1337 (lightdm) 
[ply-boot-server.c]                ply_boot_connection_on_request:got quit --retain-splash request 
[main.c]                       get_cache_file_for_mode:returning cache file '/var/lib/plymouth//boot-duration' 
[main.c]                                       on_quit:time to quit, closing log 
[main.c]                                       on_quit:deactivating keyboard 
[main.c]                                       on_quit:unloading splash 
[ply-boot-splash.c]                   ply_boot_splash_become_idle:telling splash to become idle 
[main.c]                           on_boot_splash_idle:boot splash idle 
[main.c]                           on_boot_splash_idle:quitting splash 
[main.c]                                   quit_splash:quiting splash 
[main.c]                                   quit_splash:freeing splash 
[ply-boot-splash.c]                          ply_boot_splash_free:freeing splash 
[ply-boot-splash.c]                               remove_displays:removing pixel displays 
[ply-boot-splash.c]                               remove_displays:removing text displays 
[ply-boot-splash.c]                               remove_displays:Removing 80x25 text display 
[ply-boot-splash.c]                               remove_displays:Removing node 
[./plugin.c]                                destroy_plugin:destroying plugin 
[./plugin.c]                            hide_splash_screen:hiding splash screen 
[./plugin.c]                        detach_from_event_loop:detaching from event loop 
[main.c]                                   quit_splash:removing displays and keyboard 
[main.c]                  remove_displays_and_keyboard:removing displays and keyboard 
[main.c]                  remove_displays_and_keyboard:removing text display 
[main.c]                  remove_displays_and_keyboard:removing keyboard 
[ply-terminal.c]                            ply_terminal_close:restoring color palette 
[ply-terminal.c]                            ply_terminal_close:stop watching tty fd 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 9 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 9 
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:no more destinations remaing for fd 9, removing source 
[ply-terminal.c]                            ply_terminal_close:stop watching SIGWINCH signal 
[ply-terminal.c]                            ply_terminal_close:setting buffered input 
[main.c]                           on_boot_splash_idle:quitting program 
[main.c]                                  quit_program:exiting event loop 
[ply-boot-server.c]          ply_boot_connection_on_quit_complete:quit complete 
[main.c]                                          main:exited event loop 
[ply-boot-splash.c]                          ply_boot_splash_free:freeing splash 
[main.c]                                          main:freeing terminal session 
[ply-terminal-session.c]             ply_terminal_session_stop_logging:stopping logging of incoming console messages 
[main.c]                                          main:exiting with code 0
```

Thanks in advance

---

### Post by dino99 on 2013-01-15
check your boot line to see if "splash" exist (sudo gedit /etc/default/grub)

and/or from synaptic: purge then reinstall plymouth and the dependencies

---

### Post by lepusfelix on 2013-01-15
I chose to 'reinstall' plymouth, as a complete removal was going to uninstall almost everything I ever use. Going to check now if it works ok.

UPDATE: Nope. Still no action.

---

