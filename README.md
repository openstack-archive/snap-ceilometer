# Ceilometer Snap

This repository contains the source code of the snap for the OpenStack Data
Collection service, Ceilometer.

## Installing this snap

The ceilometer snap can be installed directly from the snap store:

    sudo snap install [--edge] ceilometer

## Configuring Ceilometer

Snaps run in an AppArmor and seccomp confined profile, so don't read
configuration from `/etc/ceilometer` on the hosting operating system install.

This snap supports configuration via the $SNAP\_COMMON writable area for the
snap:

    etc
    ├── ceilometer
    │   ├── ceilometer.conf
    └── ceilometer.conf.d
        └── ceilometer-snap.conf

The ceilometer daemons (api, collector, agent-notification, agent-central)
can be configured in a few ways.

Firstly each daemon will detect and read `etc/ceilometer/ceilometer.conf`.

Alternatively all daemons will load all configuration files from
`etc/ceilometer.conf.d` if needed.

For reference, $SNAP\_COMMON is typically located under
`/var/snap/ceilometer/common`.

## Managing Ceilometer

Currently all snap binaries must be run as root; for example, to run the
ceilometer-api binary use:

    sudo ceilometer.manage

## Restarting Ceilometer services

To restart all ceilometer services:

    sudo systemctl restart snap.ceilometer.*

or use the individual service name:

    sudo systemctl restart snap.ceilometer.api
    sudo systemctl restart snap.ceilometer.agent-central

## Building the Ceilometer snap

Simply clone this repository and then install and run snapcraft:

    git clone https://github.com/openstack-snaps/snap-ceilometer
    sudo apt install snapcraft
    cd snap-ceilometer
    snapcraft

## Support

Please report any bugs related to this snap on
[Launchpad](https://bugs.launchpad.net/snap-ceilometer/+filebug).

Alternatively you can find the OpenStack Snap team in `#openstack-snaps`
on Freenode IRC.
