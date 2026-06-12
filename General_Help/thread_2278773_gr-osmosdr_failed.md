---
title: "gr-osmosdr failed"
date: 2015-05-19
forum: General Help
---

### Post by nur3 on 2015-05-19
hi. i am use ubuntu 12.04 and installing gnuradio from source using this command 
wget [http://www.sbrac.org/files/build-gnuradio](http://www.sbrac.org/files/build-gnuradio) && chmod a+x ./build-gnuradio && ./build-gnuradio --verbose


bbladeRF_test_rx_discont.dir/__/__/__/common/src/conversions.c.o
Linking C executable ../../../output/libbladeRF_test_rx_discont
[ 52%] Built target libbladeRF_test_rx_discont
Scanning dependencies of target libbladeRF_test_sync
[ 53%] Building C object
libraries/libbladeRF_test/test_sync/CMakeFiles/libbladeRF_test_sync.dir/src/main.c.o
[ 54%] Building C object
libraries/libbladeRF_test/test_sync/CMakeFiles/libbladeRF_test_sync.dir/src/test.c.o
[ 55%] Building C object
libraries/libbladeRF_test/test_sync/CMakeFiles/libbladeRF_test_sync.dir/__/__/__/common/src/conversions.c.o
[ 56%] Building C object
libraries/libbladeRF_test/test_sync/CMakeFiles/libbladeRF_test_sync.dir/__/__/__/common/src/log.c.o
Linking C executable ../../../output/libbladeRF_test_sync
[ 56%] Built target libbladeRF_test_sync
Scanning dependencies of target libbladeRF_test_timestamps
[ 57%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/main.c.o
[ 58%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_timestamps.c.o
[ 58%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_rx_gaps.c.o
[ 59%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_rx_scheduled.c.o
[ 60%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_tx_onoff.c.o
[ 61%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_tx_onoff_nowsched.c.o
[ 62%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_tx_gmsk_bursts.c.o
[ 63%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_loopback_onoff.c.o
[ 64%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_loopback_onoff_zp.c.o
[ 65%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/loopback.c.o
[ 65%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_format_mismatch.c.o
[ 66%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_readback.c.o
[ 67%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/src/test_print_timestamps.c.o
[ 68%] Building C object
libraries/libbladeRF_test/test_timestamps/CMakeFiles/libbladeRF_test_timestamps.dir/__/__/__/common/src/conversions.c.o
Linking C executable ../../../output/libbladeRF_test_timestamps
[ 68%] Built target libbladeRF_test_timestamps
Scanning dependencies of target libbladeRF_test_unused_sync
[ 69%] Building C object
libraries/libbladeRF_test/test_unused_sync/CMakeFiles/libbladeRF_test_unused_sync.dir/main.c.o
Linking C executable ../../../output/libbladeRF_test_unused_sync
[ 69%] Built target libbladeRF_test_unused_sync
[ 70%] Generating src/cmd/doc/cmd_help.h
Scanning dependencies of target bladeRF-cli
[ 70%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/main.c.o
[ 71%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/common.c.o
[ 72%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/calibrate.c.o
[ 73%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/calibrate_dc.c.o
[ 74%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/cmd.c.o
[ 75%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/erase.c.o
[ 76%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/flash_backup.c.o
[ 77%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/flash_image.c.o
[ 77%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/flash_init_cal.c.o
[ 78%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/flash_restore.c.o
[ 79%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/info.c.o
[ 80%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/load.c.o
[ 81%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/open.c.o
[ 82%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/peek.c.o
[ 83%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/lms_reg_info.c.o
[ 84%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/peekpoke.c.o
[ 84%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/poke.c.o
[ 85%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/printset.c.o
[ 86%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/probe.c.o
[ 87%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/xb.c.o
[ 88%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/xb100.c.o
[ 89%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/xb200.c.o
[ 90%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/recover.c.o
[ 91%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/rx.c.o
[ 91%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/rxtx.c.o
[ 92%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/tx.c.o
[ 93%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/version.c.o
[ 94%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/jump_boot.c.o
[ 95%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/cmd/mimo.c.o
[ 96%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/input/input.c.o
[ 97%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/input/script.c.o
[ 98%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/__/__/common/src/conversions.c.o
[ 98%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/__/__/common/src/log.c.o
[ 99%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/__/__/common/src/str_queue.c.o
[100%] Building C object
utilities/bladeRF-cli/CMakeFiles/bladeRF-cli.dir/src/input/fgets.c.o
Linking C executable ../../output/bladeRF-cli
[100%] Built target bladeRF-cli
[ 25%] Built target libbladerf_shared
[ 26%] Built target libbladeRF_test_async
[ 28%] Built target libbladeRF_test_bootloader_recovery
[ 29%] Built target libbladeRF_test_c
[ 29%] Built target libbladeRF_test_cpp
[ 41%] Built target libbladeRF_test_ctrl
[ 44%] Built target libbladeRF_test_freq_hop
[ 46%] Built target libbladeRF_test_fw_check
[ 47%] Built target libbladeRF_test_open
[ 48%] Built target libbladeRF_test_peripheral_timing
[ 51%] Built target libbladeRF_test_repeater
[ 52%] Built target libbladeRF_test_rx_discont
[ 56%] Built target libbladeRF_test_sync
[ 68%] Built target libbladeRF_test_timestamps
[ 69%] Built target libbladeRF_test_unused_sync
[100%] Built target bladeRF-cli
Install the project...
-- Install configuration: "Release"
-- Installing: /usr/local/lib/pkgconfig/libbladeRF.pc
-- Installing: /usr/local/lib/libbladeRF.so.1
-- Up-to-date: /usr/local/lib/libbladeRF.so
-- Installing: /usr/local/include/libbladeRF.h
-- Installing: /etc/udev/rules.d/88-nuand.rules
-- Installing: /usr/local/bin/bladeRF-cli
-- Removed runtime path from "/usr/local/bin/bladeRF-cli"
Done building bladeRF
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
-- checking for module 'libusb-1.0'
--   found libusb-1.0, version 1.0.9-rc3
-- Found LIBUSB: /usr/lib/x86_64-linux-gnu/libusb-1.0.so
-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE
-- Udev rules not being installed, install them with
-DINSTALL_UDEV_RULES=ON
-- Configuring done
-- Generating done
-- Build files have been written to: /home/user/airspy/host/build
Scanning dependencies of target airspy
[  7%] Building C object libairspy/src/CMakeFiles/airspy.dir/airspy.c.o
[ 14%] Building C object
libairspy/src/CMakeFiles/airspy.dir/iqconverter_float.c.o
[ 21%] Building C object
libairspy/src/CMakeFiles/airspy.dir/iqconverter_int16.c.o
Linking C shared library libairspy.so
[ 21%] Built target airspy
Scanning dependencies of target airspy-static
[ 28%] Building C object
libairspy/src/CMakeFiles/airspy-static.dir/airspy.c.o
[ 35%] Building C object
libairspy/src/CMakeFiles/airspy-static.dir/iqconverter_float.c.o
[ 42%] Building C object
libairspy/src/CMakeFiles/airspy-static.dir/iqconverter_int16.c.o
Linking C static library libairspy.a
[ 42%] Built target airspy-static
Scanning dependencies of target airspy_gpio
[ 50%] Building C object
airspy-tools/src/CMakeFiles/airspy_gpio.dir/airspy_gpio.c.o
Linking C executable airspy_gpio
[ 50%] Built target airspy_gpio
Scanning dependencies of target airspy_gpiodir
[ 57%] Building C object
airspy-tools/src/CMakeFiles/airspy_gpiodir.dir/airspy_gpiodir.c.o
Linking C executable airspy_gpiodir
[ 57%] Built target airspy_gpiodir
Scanning dependencies of target airspy_info
[ 64%] Building C object
airspy-tools/src/CMakeFiles/airspy_info.dir/airspy_info.c.o
Linking C executable airspy_info
[ 64%] Built target airspy_info
Scanning dependencies of target airspy_lib_version
[ 71%] Building C object
airspy-tools/src/CMakeFiles/airspy_lib_version.dir/airspy_lib_version.c.o
Linking C executable airspy_lib_version
[ 71%] Built target airspy_lib_version
Scanning dependencies of target airspy_r820t
[ 78%] Building C object
airspy-tools/src/CMakeFiles/airspy_r820t.dir/airspy_r820t.c.o
Linking C executable airspy_r820t
[ 78%] Built target airspy_r820t
Scanning dependencies of target airspy_rx
[ 85%] Building C object
airspy-tools/src/CMakeFiles/airspy_rx.dir/airspy_rx.c.o
Linking C executable airspy_rx
[ 85%] Built target airspy_rx
Scanning dependencies of target airspy_si5351c
[ 92%] Building C object
airspy-tools/src/CMakeFiles/airspy_si5351c.dir/airspy_si5351c.c.o
Linking C executable airspy_si5351c
[ 92%] Built target airspy_si5351c
Scanning dependencies of target airspy_spiflash
[100%] Building C object
airspy-tools/src/CMakeFiles/airspy_spiflash.dir/airspy_spiflash.c.o
Linking C executable airspy_spiflash
[100%] Built target airspy_spiflash
[ 21%] Built target airspy
[ 42%] Built target airspy-static
[ 50%] Built target airspy_gpio
[ 57%] Built target airspy_gpiodir
[ 64%] Built target airspy_info
[ 71%] Built target airspy_lib_version
[ 78%] Built target airspy_r820t
[ 85%] Built target airspy_rx
[ 92%] Built target airspy_si5351c
[100%] Built target airspy_spiflash
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib/pkgconfig/libairspy.pc
-- Installing: /usr/local/lib/libairspy.so.1.0.5
-- Up-to-date: /usr/local/lib/libairspy.so.0
-- Up-to-date: /usr/local/lib/libairspy.so
-- Installing: /usr/local/lib/libairspy.a
-- Installing: /usr/local/include/libairspy/airspy.h
-- Installing: /usr/local/include/libairspy/airspy_commands.h
-- Installing: /usr/local/include/libairspy/iqconverter_float.h
-- Installing: /usr/local/include/libairspy/iqconverter_int16.h
-- Installing: /usr/local/include/libairspy/filters.h
-- Installing: /usr/local/bin/airspy_gpio
-- Removed runtime path from "/usr/local/bin/airspy_gpio"
-- Installing: /usr/local/bin/airspy_gpiodir
-- Removed runtime path from "/usr/local/bin/airspy_gpiodir"
-- Installing: /usr/local/bin/airspy_lib_version
-- Removed runtime path from "/usr/local/bin/airspy_lib_version"
-- Installing: /usr/local/bin/airspy_si5351c
-- Removed runtime path from "/usr/local/bin/airspy_si5351c"
-- Installing: /usr/local/bin/airspy_r820t
-- Removed runtime path from "/usr/local/bin/airspy_r820t"
-- Installing: /usr/local/bin/airspy_spiflash
-- Removed runtime path from "/usr/local/bin/airspy_spiflash"
-- Installing: /usr/local/bin/airspy_info
-- Removed runtime path from "/usr/local/bin/airspy_info"
-- Installing: /usr/local/bin/airspy_rx
-- Removed runtime path from "/usr/local/bin/airspy_rx"
Done building airspy
Building gr-osmosdr...-- The CXX compiler identification is GNU
-- The C compiler identification is GNU
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Build type not specified: defaulting to release.
-- Found Git: /usr/bin/git
-- Extracting version information from git describe...
-- Configuring Boost C++ Libraries...
-- Boost version: 1.48.0
-- Found the following Boost libraries:
--   thread
--   system
Checking for GNU Radio Module: RUNTIME
-- checking for module 'gnuradio-runtime'
--   found gnuradio-runtime, version 3.7.7.1
 * INCLUDES=/usr/local/include
 *
LIBS=/usr/local/lib/libgnuradio-runtime.so;/usr/local/lib/libgnuradio-pmt.so
-- Found GNURADIO_RUNTIME:
/usr/local/lib/libgnuradio-runtime.so;/usr/local/lib/libgnuradio-pmt.so
GNURADIO_RUNTIME_FOUND = TRUE
Checking for GNU Radio Module: BLOCKS
-- checking for module 'gnuradio-blocks'
--   found gnuradio-blocks, version 3.7.7.1
 * INCLUDES=/usr/local/include
 *
LIBS=/usr/local/lib/libgnuradio-blocks.so;/usr/local/lib/libgnuradio-runtime.so;/usr/local/lib/libgnuradio-pmt.so
-- Found GNURADIO_BLOCKS:
/usr/local/lib/libgnuradio-blocks.so;/usr/local/lib/libgnuradio-runtime.so;/usr/local/lib/libgnuradio-pmt.so
GNURADIO_BLOCKS_FOUND = TRUE
Checking for GNU Radio Module: PMT
-- checking for module 'gnuradio-runtime'
--   found gnuradio-runtime, version 3.7.7.1
 * INCLUDES=/usr/local/include
 *
LIBS=/usr/local/lib/libgnuradio-runtime.so;/usr/local/lib/libgnuradio-pmt.so
-- Found GNURADIO_PMT:
/usr/local/lib/libgnuradio-runtime.so;/usr/local/lib/libgnuradio-pmt.so
GNURADIO_PMT_FOUND = TRUE
-- checking for module 'gnuradio-iqbalance'
--   found gnuradio-iqbalance, version 0
-- Found GNURADIO_IQBALANCE: /usr/local/lib/libgnuradio-iqbalance.so
-- Found UHD: /usr/local/lib/libuhd.so
-- checking for module 'gnuradio-uhd'
--   found gnuradio-uhd, version 3.7.7.1
-- Found gnuradio-uhd: /usr/local/include,
/usr/local/lib/libgnuradio-uhd.so
-- Found GNURADIO_UHD: /usr/local/lib/libgnuradio-uhd.so
-- checking for module 'gnuradio-fcd'
--   found gnuradio-fcd, version 3.7.7.1
-- Found gnuradio-fcd: /usr/local/include,
/usr/local/lib/libgnuradio-fcd.so
-- Found GNURADIO_FCD: /usr/local/lib/libgnuradio-fcd.so
-- checking for module 'gnuradio-fcdproplus'
--   package 'gnuradio-fcdproplus' not found
-- gnuradio-fcdproplus not found.
-- Could NOT find GNURADIO_FCDPP (missing:  GNURADIO_FCDPP_LIBRARIES
GNURADIO_FCDPP_INCLUDE_DIRS)
-- checking for module 'libosmosdr'
--   package 'libosmosdr' not found
-- libosmosdr not found.
-- checking for module 'librtlsdr'
--   found librtlsdr, version v0.5.3-10-g8b4d
-- Found librtlsdr: /usr/local/include, /usr/local/lib/librtlsdr.so
-- checking for module 'libmirisdr'
--   package 'libmirisdr' not found
-- libmirisdr not found.
-- checking for module 'libhackrf'
--   found libhackrf, version 0.3
-- Found LIBHACKRF: /usr/local/lib/libhackrf.so
-- checking for module 'libairspy'
--   found libairspy, version 1.0
-- Found LIBAIRSPY: /usr/local/lib/libairspy.so
-- checking for module 'libbladeRF'
--   found libbladeRF, version 1.2.1-git-48ab748
-- Found libbladeRF: /usr/local/include, /usr/local/lib/libbladeRF.so
CMake Error at CMakeLists.txt:168 (find_package):
  find_package called with invalid argument "CONFIG"


-- Found Doxygen: /usr/bin/doxygen
-- Found PythonLibs: /usr/lib/libpython2.7.so (Required is at least
version "2")
--
-- Checking for module SWIG
-- Found SWIG version 2.0.4.
-- Found SWIG: /usr/bin/swig2.0
-- Minimum SWIG version required is 1.3.31
--
-- The build system will automatically enable all components.
-- Use -DENABLE_DEFAULT=OFF to disable components by default.
--
-- Configuring Python support support...
--   Dependency PYTHONLIBS_FOUND = TRUE
--   Dependency SWIG_FOUND = TRUE
--   Dependency SWIG_VERSION_CHECK = TRUE
--   Enabling Python support support.
--   Override with -DENABLE_PYTHON=ON/OFF
--
-- Configuring high resolution timing...
-- Performing Test HAVE_CLOCK_GETTIME
-- Performing Test HAVE_CLOCK_GETTIME - Success
-- Performing Test HAVE_MACH_ABSOLUTE_TIME
-- Performing Test HAVE_MACH_ABSOLUTE_TIME - Failed
-- Performing Test HAVE_QUERY_PERFORMANCE_COUNTER
-- Performing Test HAVE_QUERY_PERFORMANCE_COUNTER - Failed
--   High resolution timing supported through clock_gettime.
--
-- Configuring Osmocom IQ Imbalance Correction support...
--   Dependency GNURADIO_IQBALANCE_FOUND = TRUE
--   Enabling Osmocom IQ Imbalance Correction support.
--   Override with -DENABLE_IQBALANCE=ON/OFF
--
-- Configuring sysmocom OsmoSDR support...
--   Dependency LIBOSMOSDR_FOUND = FALSE
--   Disabling sysmocom OsmoSDR support.
--   Override with -DENABLE_OSMOSDR=ON/OFF
--
-- Configuring FUNcube Dongle support...
--   Dependency GNURADIO_FCD_FOUND = TRUE
--   Enabling FUNcube Dongle support.
--   Override with -DENABLE_FCD=ON/OFF
--
-- Configuring FUNcube Dongle Pro+ support...
--   Dependency GNURADIO_FCDPP_FOUND = FALSE
--   Disabling FUNcube Dongle Pro+ support.
--   Override with -DENABLE_FCDPP=ON/OFF
--
-- Configuring IQ File Source support...
--   Dependency GNURADIO_BLOCKS_FOUND = TRUE
--   Enabling IQ File Source support.
--   Override with -DENABLE_FILE=ON/OFF
--
-- Configuring Osmocom RTLSDR support...
--   Dependency LIBRTLSDR_FOUND = TRUE
--   Enabling Osmocom RTLSDR support.
--   Override with -DENABLE_RTL=ON/OFF
--
-- Configuring RTLSDR TCP Client support...
--   Dependency GNURADIO_BLOCKS_FOUND = TRUE
--   Enabling RTLSDR TCP Client support.
--   Override with -DENABLE_RTL_TCP=ON/OFF
--
-- Configuring Ettus USRP Devices support...
--   Dependency UHD_FOUND = TRUE
--   Dependency GNURADIO_UHD_FOUND = TRUE
--   Enabling Ettus USRP Devices support.
--   Override with -DENABLE_UHD=ON/OFF
--
-- Configuring Osmocom MiriSDR support...
--   Dependency LIBMIRISDR_FOUND = FALSE
--   Disabling Osmocom MiriSDR support.
--   Override with -DENABLE_MIRI=ON/OFF
--
-- Configuring HackRF Jawbreaker support...
--   Dependency LIBHACKRF_FOUND = TRUE
--   Enabling HackRF Jawbreaker support.
--   Override with -DENABLE_HACKRF=ON/OFF
--
-- Configuring nuand bladeRF support...
--   Dependency LIBBLADERF_FOUND = TRUE
--   Enabling nuand bladeRF support.
--   Override with -DENABLE_BLADERF=ON/OFF
--
-- Configuring RFSPACE Receivers support...
--   Enabling RFSPACE Receivers support.
--   Override with -DENABLE_RFSPACE=ON/OFF
--
-- Configuring AIRSPY Receiver support...
--   Dependency LIBAIRSPY_FOUND = TRUE
--   Enabling AIRSPY Receiver support.
--   Override with -DENABLE_AIRSPY=ON/OFF
--
-- Configuring SoapySDR support support...
--   Dependency SoapySDR_FOUND =
--   Disabling SoapySDR support support.
--   Override with -DENABLE_SOAPY=ON/OFF
-- Found PythonInterp: /usr/bin/python (found suitable version "2.7.3",
required is "2")
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of size_t
-- Check size of size_t - done
-- Check size of unsigned int
-- Check size of unsigned int - done
-- Performing Test HAVE_WNO_UNUSED_BUT_SET_VARIABLE
-- Performing Test HAVE_WNO_UNUSED_BUT_SET_VARIABLE - Success
--
-- ######################################################
-- # Gnuradio enabled components
-- ######################################################
--   * Python support
--   * Osmocom IQ Imbalance Correction
--   * FUNcube Dongle
--   * IQ File Source
--   * Osmocom RTLSDR
--   * RTLSDR TCP Client
--   * Ettus USRP Devices
--   * HackRF Jawbreaker
--   * nuand bladeRF
--   * RFSPACE Receivers
--   * AIRSPY Receiver
######################################################
-- # Gnuradio disabled components
-- ######################################################
--   * sysmocom OsmoSDR
--   * FUNcube Dongle Pro+
--   * Osmocom MiriSDR
--   * SoapySDR support
--
-- Building for version: v0.1.4-29-g44c223cb / 0.1.5git
-- Using install prefix: /usr/local
-- Configuring incomplete, errors occurred!
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.

gr-osmosdr build apparently failed
Exit rtl-sdr/gr-osmosdr build

=======================================================================
If you have found this script useful and time-saving, consider a
donation to help me keep build-gnuradio, simple_ra, SIDsuite,
meteor_detector, simple_fm_rcv, and multimode maintained and up to date.
A simple paypal transfer to [EMAIL="mleech@ripnet.com"]mleech@ripnet.com[/EMAIL] is all you need to do.
======================================================================
Send success/fail info to sbrac.org?n


what can i do?i hope you can help me.
thanks

---

### Post by dino99 on 2015-05-19
you can get it from the ubuntu archives: [https://launchpad.net/ubuntu/+source/gnuradio](https://launchpad.net/ubuntu/+source/gnuradio)

---

