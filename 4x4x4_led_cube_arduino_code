# envisage_project
#arduino_code
int data_pin = 12;
int clk_pin = 11;

void setup() 
{
  pinMode(data_pin,OUTPUT);
  pinMode(clk_pin,OUTPUT);
}

void loop() 
{
  all_off();
  all_on();
  flicker_on();
  flicker_off();
  random_flicker();
  rain();
  spiral();
}

void shift_out(byte data)
{
  shiftOut(data_pin,clk_pin,LSBFIRST,data);
  shiftOut(data_pin,clk_pin,LSBFIRST,data>>8);
  shiftOut(data_pin,clk_pin,LSBFIRST,data>>8); 
}
void all_on()
{
  byte data = 000000000000000000001111;
  shift_out(data);
}
void all_off()
{
   byte data = 111111111111111100000000;
   shift_out(data);
}
void flicker_on()
{
  all_on();
  delay(150);  
  for(int t = 150;t >= 0;t -= 5)
  {
    all_off();
    delay(t);
    all_on();
    delay(t);
  }
}
void flicker_off() 
{
  all_on();
  for(int t = 0;t <= 150; t += 5)
  {
    all_off();
    delay(t+50);
    all_on();
    delay(t);
  }
}
void random_flicker()
{
  all_off();
  int x = 10;
  delay(x);
  for(int i = 0;i <= 750; i += 2)
  {
    int layer_select = random(0,4);
    int column_select = random(0,16);
    shiftOut(data_pin,clk_pin,LSBFIRST,1<<layer_select);
    if(column_select < 8)
    {
      shiftOut(data_pin,clk_pin,LSBFIRST,1<<column_select);  
    }
    else
    {
      shiftOut(data_pin,clk_pin,LSBFIRST,0);
      shiftOut(data_pin,clk_pin,LSBFIRST,1<<column_select-8);  
    }
    delay(x);
    all_off();
    delay(x);
  }
}
void rain()
{
  all_off();
  int x=100;
  for(i=0;i<=30;i+=1)
  {
    int column_select = random(0,16);
    for(layer_select=3;layer_select>=0;layer_select--)
    {
      shiftOut(data_pin,clk_pin,LSBFIRST,1<<layer_select);
      if(column_select < 8)
      {
        shiftOut(data_pin,clk_pin,LSBFIRST,1<<column_select);  
      }
      else
      {
        shiftOut(data_pin,clk_pin,LSBFIRST,0);
        shiftOut(data_pin,clk_pin,LSBFIRST,1<<column_select-8);  
      }
     }
  }
}
void spiral()
{
  all_off();
  byte data[16]= {111111111111111000001111,111111111111110100001111,111111111111101100001111,111111111111011100001111,111111110111111100001111,111101111111111100001111,011111111111111100001111,
                101111111111111100001111,110111111111111100001111,111011111111111100001111,111111101111111100001111,111111111110111100001111,111111111110111100001111,111111111101111100001111,
                111111011111111100001111,111111101111111100001111}
  for(int i = 0;i < 16;i++)
  {
    shift_out(data[i]);
    delay(100);
  }
  for(int i = 15; i >= 0;i--)
  {
    shift_out(data[i]);
    delay(100);  
  }  
}
  
