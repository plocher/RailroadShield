A community prototyping board to help with the bringup and maturation of OpenLCB.


Status: Prototypes fab'd and assembled, runs simple OpenLCB sketches, more testing underway in the OpenLCB community...


This project is an Arduino shield for Loconet, CAN and
[http://www.olcb.org/ OpenLCB] experimentation.  It is based on an
earlier set of experiments that only supported CAN and Loconet as
part of a custom 'duino stack which was used to build a [[ControlPoint]]
demo for the PCR Coast Division meet early in September, 2010.


I also spun solderless breadboard versions of the CANBusBreadboard
and LoconetBreadboard; the Loconet board works fine, but I have not
yet (2010) built and tested the CAN board.


The prototype served its purpose - it helped prove out the design
pattern of a local control point node that uses a local Loconet to
monitor occupancy detectors, turnouts and other "vital" logic as
well as control signals associated with the interlocking.  I built
a small handful of 8- and 16-bit I2C based I/O expander boards
(think mini-C/MRI) to make interfacing with control panels and LEDs
easier, but the power draw of 30 to 60 LEDs - even at 10mA ea - is
almost too much for the simple heatsinked 7805 linear regulator I
designed into the main board.  Better to use a distributed power
supply design, which means another design/fab cycle and more boards
in my junk drawer :-)


As in the real world, the control point passed Controls and Indications
back and forth along a code line; in the 1.0 demo, I used OPC_PEER_XFER
Loconet packets to emulate a code line; the next step is to use
CAN/openLCB instead.

The RailroadShield board is based on an expanded footprint Arduino
Shield template so that Decimila, Uno and Duemilanove boards can
easily be used with it.

This design has hardware support for

  * DCC  on D8,
  *  * See [http://www.nmra.org/standards/DCC/standards_rps/DCCStds.html NMRA DCC Standards] documentation
  * Loconet (RXD on D8, Lnet TXD on D7)
  *  * See Digitrax's [Loconet Personal Edition](http://www.digitrax.com/ftp/loconetpersonaledition.pdf)
  * CAN/openLCB using MCP2515 & MCP2551 on D13-D11,D9 & D3
  *  * See [OpenLCB info](http://openlcb.org/trunk/prototypes/Hobbyists.html)
  * RS485 full duplex/2 wire (NCE & XPressNet) or half duplex/4 wire (C/MRI) using the built in UART on D0/D1 with TX enable on D5
  *  * See Lenz's XpressNet: [Specification](http://www.lenz.com/manuals/xpressnet/xpressnet.pdf) and
  *  * NCE's cab bus [on page 32 of the Power Pro System Reference Manual](http://www.ncedcc.com/images/stories/manuals/sysman07.pdf)
  * 4 buttons+LEDs for simple I/O testing.

Let me know if you develop sketches or libraries for the above and
I will update this page with links.  Better yet, contribute the
code back to the openlcb.org openLCB project.

