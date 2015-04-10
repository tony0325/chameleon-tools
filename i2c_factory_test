#!/usr/bin/python
"""
This is tonycwlin@'s first Python to help factory scan i2c devices @ Chameleon B1/B2 board
Todo: tonycwlin@ to scan BT module.
"""
import os
import sys
import subprocess

def main():
    """Entry point, start to scan bus 0 """
    print '\n..................................................\n'
    os.system('/home/root/io init')
    check_FRAM()
    bus = 0
    component_miss_in_bus0 = 0
    component_miss_in_bus3 = 0
    print 'Checking I2C devices on BUS' + str(bus) + '------------->'
    real_result = i2cprobe(bus)
#    required_items = ['20', '21', '23']
#    missing_items = set(required_items) - set(real_result)
#    if missing_items:
#        print 'missing: %s' % missing_items
    if '20' not in real_result:
        print 'I/O expander(U43) 0x20 is not on i2c BUS0 !!! '
        component_miss_in_bus0 += 1 
    if '21' not in real_result:
        print 'I/O expander(U44) 0x21 is not on i2c BUS0 !!! '
        component_miss_in_bus0 += 1 
    if '48' not in real_result:
        print 'IT6803(U53) 0x48 is not on i2c BUS0 !!! '
        component_miss_in_bus0 += 1 
    if '4c' not in real_result:
        print 'CAT9883C(U9) 0x4c is not on i2c BUS0 !!! '
        component_miss_in_bus0 += 1 
    if '54' not in real_result:
        print 'EEPROM(U54) 0x54 is not on i2c BUS0 !!! '
        component_miss_in_bus0 += 1 
    if '58' not in real_result:
        print 'IT6506(U1) 0x58 is not on i2c BUS0 !!! '
        component_miss_in_bus0 += 1 
    if '59' not in real_result:
        print 'IT6506(U5) 0x59 is not on i2c BUS0 !!! '
        component_miss_in_bus0 += 1 
    if '70' not in real_result:
        print '0x70 is not on i2c BUS0 !!! '
        component_miss_in_bus0 += 1 
    if '71' not in real_result:
        print '0x71 is not on i2c BUS0 !!! '
        component_miss_in_bus0 += 1 
    if component_miss_in_bus0 == 0: 
        print 'OK.\n'
        
#    print 'Total lost I2C components on BUS0 = ' + str(component_miss_in_bus0)
  
    """Start to scan bus 3 """
    bus = 3
    print 'Checking I2C devices on BUS' + str(bus) + '------------->'
    real_result = i2cprobe(bus)
    if '20' not in real_result:
        print 'I/O expander(U2) 0x20 is not on i2c BUS3 !!! '
        component_miss_in_bus3 += 1 
    if '21' not in real_result:
        print 'I/O expander(U18) 0x21 is not on i2c BUS3 !!! '
        component_miss_in_bus3 += 1 
    if '22' not in real_result:
        print 'I/O expander(U19) 0x22 is not on i2c BUS3 !!! '
        component_miss_in_bus3 += 1 
    if '2f' not in real_result:
        print 'Digital Potentiometer(U21) 0x2f is not on i2c BUS3 !!! '
        component_miss_in_bus3 += 1 
    if '40' not in real_result:
        print 'INA219(U8) 0x40 is not on i2c BUS3 !!! '
        component_miss_in_bus3 += 1 
    if '44' not in real_result:
        print 'INA219(U9) 0x44 is not on i2c BUS3 !!! '
        component_miss_in_bus3 += 1 
    if component_miss_in_bus3 == 0:
        print "OK.\n"
    
#    print 'Total lost I2C components on BUS3 = ' + str(component_miss_in_bus3)
    print "..................................................\n"

def check_FRAM():
    os.system('/home/root/io fram dp1')
    print 'Checking FRAM of DP1------>'
    check_FRAM_result = i2cprobe(0)
    if '50' not in check_FRAM_result:
        print 'FRAM(U54) of DP1 is not found !!!'
    else:
        print 'OK.\n'
    os.system('/home/root/io fram dp2')
    print 'Checking FRAM of DP2------>'
    check_FRAM_result = i2cprobe(0)
    if '50' not in check_FRAM_result:
        print 'FRAM(U56) of DP2 is not found !!!'
    else:
        print 'OK.\n'
    os.system('/home/root/io fram none')

def i2cprobe(bus):
    cmd = ['/home/root/i2c', 'probe', '%x' % bus]
    out = subprocess.check_output(cmd)
    split_out = out.split('\n')
    return split_out

if __name__ == '__main__':
    main()
