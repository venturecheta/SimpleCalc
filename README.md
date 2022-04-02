# SimpleCalc
// SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.0;

contract TheSuperBasicCalc {

    uint256 public x; // state variable
    uint256 public xy;

    modifier xyFilter() {
        require (xy == 1, "xy is not 1");
        _;
    }


    function setXY(uint256 _xy) external {
        xy = _xy;
    }

    function calculatorWithoutParams() external xyFilter returns(uint256) {
        x = 1 + 3; // hardcoded
        return x;
    }

    function calculatorWithParams(uint256 _x1, uint256 _x2) external returns(uint256) {
        x = _x1 + _x2;
        return x;
    }

    function getX() external view returns (uint256) {
        return x;
    }

    function add(uint a, uint b) public {
        x = a + b;
    }

    function sub(uint a, uint b) public {
        x = a - b;
    }

    function mul(uint a, uint b) public {
        x = a * b;
    }

    function div(uint a, uint b) public {
        require(b > 0, "The second parameter should be larger than 0");

        x = a / b;
    }

    function getResult() public view returns (uint256) {
        return x;
    }
}
