# Build KDE Plasma5 on Debian 10

## Qt 5.15.x

### Dependencies

To install dependencies just run below command:

```bash
sudo apt-get install assimp-utils ccache default-libmysqlclient-dev ffmpeg ffmpegthumbnailer flite1-dev g++ gcc git gperf icu-devtools libassimp-dev libavc1394-dev libavcodec-dev libavdevice-dev libavfilter-dev libavformat-dev libavresample-dev libavutil-dev libbluetooth-dev libclang-dev libcups2-dev libdbus-1-dev libdbus-c++-dev libdouble-conversion-dev libdrm-dev libevent-dev libffmpegthumbnailer-dev libfontconfig1-dev libfreetype6-dev libgif-dev libgstreamer-plugins-bad1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev libgstreamermm-1.0-dev libgtk-3-dev libgtk2.0-dev libharfbuzz-dev libiconv-hook-dev libicu-dev libinput-dev libjsoncpp-dev liblcms2-dev libmariadbclient-dev libminizip-dev libmng-dev libmtdev-dev libmysqlcppconn-dev libnss3-dev libodb-dev libodbc1 libopenal-dev libopus-dev libopusfile-dev libpcre2-dev libpng-dev libpoppler-cpp-dev libpoppler-dev libpostproc-dev libpq-dev libprotobuf-dev libproxy-dev libpulse-dev libre2-dev libsctp-dev libsdl2-dev libsensors4-dev libsnappy-dev libspeechd-dev libsqlite0-dev libsqlite3-dev libssl-dev libswresample-dev libswscale-dev libsybdb5 libtdb-dev libtiff-dev libts-dev libudev-dev libvpx-dev libvulkan-dev libwebp-dev libx11-dev libx11-xcb-dev libxcb-glx0-dev libxcb-icccm4-dev libxcb-image0-dev libxcb-keysyms1-dev libxcb-randr0-dev libxcb-render-util0-dev libxcb-shape0-dev libxcb-shm0-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb-xinerama0-dev libxcb-xinput-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxext-dev libxfixes-dev libxi-dev libxkbcommon-dev libxkbcommon-x11-dev libxml2-dev libxrender-dev libxslt1-dev libxtst-dev libzstd-dev make ninja-build nodejs odbcinst opus-tools protobuf-compiler re2c speech-dispatcher syslog-ng-dev unixodbc-dev libgpgme-dev
```

### Build

Download, Extract and build Qt 5.15 using below command:

```bash
wget -c http://download.qt.io/official_releases/qt/5.15/5.15.1/single/qt-everywhere-src-5.15.1.tar.xz
tar -xvf qt-everywhere-src-5.15.1.tar.xz
cd qt-everywhere-src-5.15.1

export ELFUTILS_INSTALL_DIR=/usr/bin
export QTC_ENABLE_CLANG_LIBTOOLING=true
export LLVM_INSTALL_DIR=/usr/lib/llvm-7
export PATH="$LLVM_INSTALL_DIR/bin/:$PATH"

./configure -prefix /opt/kde -confirm-license -opensource -nomake tests -nomake examples -release
make -j2
sudo make install
```



## KDE Plasma 5.20

### Dependencies from Repository

You could install some dependencies from official repository:

```bash
sudo apt-get install appmenu-gtk2-module appmenu-gtk3-module bolt catdoc check dbus-test-runner dialog docbook-xml docbook-xsl* fonts-hack* fonts-noto* gobject-introspection gtk-doc-tools gtk2-engines-pixbuf intltool libaccounts-glib-dev libacl1-dev libappimage-dev libarchive13 libattr1-dev libavahi-client-dev libavahi-common-dev libavahi-core-dev libcanberra-dev libcanberra-pulse libcap-dev libcommon-sense-perl libdbus-glib-1-dev libdbusmenu-qt5-2 libdmtx-dev libecm-dev libencode-locale-perl libepub-dev libevdev-dev libevent-dev libexiv2-dev libfile-listing-perl libflatpak-dev libgcrypt20-dev libgirepository1.0-dev libgit2-dev libgps-dev libgssapi-perl libgtk2.0-dev libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhyphen-dev libical-dev libimobiledevice-dev libinput-dev libio-html-perl libio-socket-ssl-perl libjson-xs-perl liblmdb++-dev liblmdb-dev liblwp-mediatypes-perl liblwp-protocol-https-perl libmm-dev libmtp-dev libnet-http-perl libnet-ssleay-perl libnm-dev libopenconnect-dev libpackagekit-glib2-dev libpam0g-dev libpcap-dev libpci-dev libpipewire-0.2-dev libplist++-dev libplist-dev libpolkit-agent-1-dev libpolkit-backend-1-dev libpoppler-dev libpwquality-dev libqalculate-dev libqrencode-dev librhash0 libsass-dev libscim-dev libsnapd-glib-dev libsoup2.4-dev libssh-dev libstemmer-dev libtag-extras-dev libtag1-dev libtimedate-perl libtirpc-dev libtry-tiny-perl libtypes-serialiser-perl libvlc-dev libvlccore-dev libwayland-dev libwww-perl libwww-robotrules-perl libx11-dev libx11-xcb-dev libxcb-composite0-dev libxcb-cursor-dev libxcb-damage0-dev libxcb-dpms0-dev libxcb-res0-dev libxcb-util0-dev libxcb-xtest0-dev libxcb1-dev libxml-parser-perl libxsettings-dev libyaml-0-2 libyaml-dev libyaml-libyaml-perl lmdb-utils media-player-info mediainfo meson mobile-broadband-provider-info modemmanager modemmanager-dev openconnect pciutils perl-openssl-defaults pipewire python-gobject python3-cairo python3-gi ruby samba-dev sass scim socat valac wayland-protocols xorg-dev xsettingsd libmission-control-plugins-dev libraw-dev ibcurl4-gnutls-dev zlib1g-dev libopenjp2-7-dev libcdparanoia-dev cdparanoia libarchive-dev libdvdread-dev libflac-dev libflac++-dev libmad0-dev libmadlib-dev musepack-tools muse libsndfile1-dev libmp3lame-dev libogg-dev libfuzzer-7-dev libvorbis-dev clang-tidy clazy cppcheck heaptrack llvm-dev libfreecell-solver-dev libvncserver-dev libeigen3-dev libaudiofile-dev libsndfile1-dev libsane-dev libhunspell-dev libfluidsynth-dev libvncserver-dev libfakekey-dev libopenbabel-dev libreadline-dev libcfitsio-dev libupnp-dev libspectre-dev libchm-dev libshp-dev libmusicbrainz5-dev libboost-system-dev libfftw3-dev frei0r-plugins-dev libjack-dev libmovit-dev libebur128-dev libsamplerate0-dev samplerate-programs librubberband-dev librtaudio-dev libsox-dev libvidstab-dev signon-plugin-oauth2-dev xserver-xorg-input-synaptics-dev xserver-xorg-input-libinput-dev xserver-xorg-input-evdev-dev appstream
```

### Dependencies needed to build

#### CMake

```bash
git clone https://github.com/Kitware/CMake.git
cd CMake/
./bootstrap --prefix /opt/kde
make -j2
sudo make install
```

#### Wayland Protocols

```bash
git clone https://github.com/wayland-project/wayland-protocols.git
cd wayland-protocols
./configure -prefix=/opt/kde
make
sudo make install
```

#### Poppler

```bash
git clone https://anongit.freedesktop.org/git/poppler/poppler.git
cd poppler
mkdir build
cd build
export PATH="/opt/kde/bin:$PATH"
cmake -DCMAKE_BUILD_TYPE=release -DCMAKE_INSTALL_PREFIX=/opt/kde ..
make -j2
sudo make install
```

#### Accounts GLib Libraries

```bash
git clone https://gitlab.com/accounts-sso/libaccounts-glib.git
cd libaccounts-glib
meson build --prefix=/opt/kde
ninja 
sudo ninja install
```

#### Grantlee

```bash
git clone https://github.com/steveire/grantlee.git
cd grantlee/
mkdir build
cd build/
export PATH="/opt/kde/bin:$PATH"
cmake -DCMAKE_BUILD_TYPE=release -DCMAKE_INSTALL_PREFIX=/opt/kde ..
make -j2
sudo make install
```

#### QWebkit

```bash
git clone https://github.com/qt/qtwebkit.git --depth 1
cd qtwebkit/
export PATH="/opt/kde/bin:$PATH"
mkdir build
cd build/
export PATH="/opt/kde/bin:$PATH"
qmake -r ..
make -j2
sudo make install
```

#### PackageKit-Qt

```bash
git clone https://github.com/hughsie/PackageKit-Qt.git
cd PackageKit-Qt/
mkdir build
cd build/
export PATH="/opt/kde/bin:$PATH"
cmake -DCMAKE_BUILD_TYPE=release -DCMAKE_INSTALL_PREFIX=/opt/kde ..
make -j2
sudo make install
```

#### AppStream

```bash
git clone https://github.com/ximion/appstream.git
cd appstream/
mkdir build
cd build/
meson --prefix=/opt/kde .. -Dqt=true 
ninja
sudo ninja install
```

#### LibSignon

```bash
git clone --recursive  https://gitlab.com/accounts-sso/libsignon-glib.git
cd libsignon-glib
mkdir build
cd build
meson --prefix=/usr ..
ninja
sudo ninja install
```

#### GpgMe

```bash
wget https://gnupg.org/ftp/gcrypt/gpgme/gpgme-1.14.0.tar.bz2
tar -xvf gpgme-1.14.0.tar.bz2
cd gpgme-1.14.0.tar.bz2
export PKG_CONFIG_PATH="/opt/kde/lib/pkgconfig/:$PKG_CONFIG_PATH"
./configure -prefix=/opt/kde
make -j2
make install
```

#### GpgMepp

```bash
git clone https://github.com/KDE/gpgmepp.git
cd gpgmepp
mkdir build
cd build/
export PATH="/opt/kde/bin:$PATH"
cmake -DCMAKE_BUILD_TYPE=release -DCMAKE_INSTALL_PREFIX=/opt/kde ..
make -j2
sudo make install
```

#### MLT

```bash
git clone --recursive https://github.com/mltframework/mlt.git --depth 1
cd mlt
export PATH="/opt/kde/bin:$PATH"
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=release -DCMAKE_INSTALL_PREFIX=/opt/kde ..
make -j2
make install
```

### Build KDE

```bash
git clone https://invent.kde.org/sdk/kdesrc-build
cd kdesrc-build/
./kdesrc-build-setup
```

Edit `~/.kdesrc-buildrc` file and add below line to the global section:

```bash
cmake-options -DCMAKE_BUILD_TYPE=release
```

Also make sure below variables set to the true values:

```bash
kdedir /opt/kde
stop-on-failure false
install-session-driver true
install-environment-driver true
```

and add below line after `end global` if not exists:

```bash
include /opt/kde
```

and then run build process:

```bash
./kdesrc-build --include-dependencies
```

## Setup KDE

After all built, You must setup DBus settings. So Edit `/etc/dbus-1/session-local.conf` file using nano and add below lines:

```xml
<busconfig>
    <servicedir>/opt/kde/usr/share/dbus-1/services</servicedir>
    <servicedir>/opt/kde/usr/share/dbus-1/system-services</servicedir>
    <includedir>/opt/kde/usr/share/dbus-1/system.d/</includedir>
</busconfig>
```

Next if you install kde on a location other than `/usr/` you must install start scripts to the system:

```bash
sudo install "/home/bardia/mnt/plasma-workspace/login-sessions/plasmax11-dev.desktop" "/usr/share/xsessions/plasma.desktop"
install "<build-dir>/plasma-workspace/prefix.sh" "/opt/kde/lib/x86_64-linux-gnu/libexec/plasma-dev-prefix.sh"
install "<build-dir>/plasma-workspace/login-sessions/startplasma-dev.sh" "/opt/kde/lib/x86_64-linux-gnu/libexec"
```

And then edit `/usr/share/xsessions/plasma.desktop` and remove `-x11` switch from the `Exec` part:

```ini
Exec=/opt/kde/lib/x86_64-linux-gnu/libexec/startplasma-dev.sh
```

And edit `/opt/kde/lib/x86_64-linux-gnu/libexec/startplasma-dev.sh` file and replace last line with:

```bash
/opt/kde/lib/x86_64-linux-gnu/libexec/kactivitymanagerd &
/opt/kde/bin/krunner &
/opt/kde/bin/kglobalaccel5 &

startplasma-x11
```

