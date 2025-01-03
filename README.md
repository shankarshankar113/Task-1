# Task-1
Here's an example of designing basic digital logic circuits using Verilog:

Logic Gates
```
module logic_gates(
    input a,
    input b,
    output and_out,
    output or_out,
    output not_out
);

assign and_out = a & b;
assign or_out = a | b;
assign not_out = ~a;

endmodule
```

Adders
```
module adder(
    input [3:0] a,
    input [3:0] b,
    output [3:0] sum,
    output carry_out
);

assign {carry_out, sum} = a + b;

endmodule
```

Multiplexers
```
module multiplexer(
    input [3:0] a,
    input [3:0] b,
    input sel,
    output [3:0] out
);

assign out = sel ? b : a;

endmodule
```

Testbench
```
module testbench;

reg [3:0] a;
reg [3:0] b;
reg sel;
wire [3:0] sum;
wire carry_out;
wire [3:0] out;

logic_gates lg(.a(a[0]), .b(b[0]), .and_out(), .or_out(), .not_out());
adder add(.a(a), .b(b), .sum(sum), .carry_out(carry_out));
multiplexer mux(.a(a), .b(b), .sel(sel), .out(out));

initial begin
    a = 4'd5;
    b = 4'd3;
    sel = 0;
    #10 sel = 1;
    #10 a = 4'd7;
    #10 b = 4'd2;
    #10 $finish;
end
endmodule
