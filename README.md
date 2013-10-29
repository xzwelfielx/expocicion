expocicion
==========

esta es nuestra expocicion


// Demostración de BorderLayout.
2 import java.awt.*;
3 import java.awt.event.*;
4 import javax.swing.*;
5 
6 public class DemoBorderLayout extends JFrame implements ActionListener
7 {
8    private JButton botones[];
9    private final String nombres[] = { "Ocultar norte", "Ocultar sur", 
10       "Ocultar este", "Ocultar oeste", "Ocultar centro" };
11    private BorderLayout esquema;
12 
13    // configurar GUI y el manejo de eventos
14    public DemoBorderLayout()
15    {
16       super( "Demostración de BorderLayout" );
17 
18       esquema = new BorderLayout( 5, 5 ); // espacios libres de 5 píxeles
19 
20       // obtener panel de contenido y establecer su esquema
21       Container contenedor = getContentPane();
22       contenedor.setLayout( esquema );
23 
24       // instanciar objetos botón
25       botones = new JButton[ nombres.length ];
26 
27       for ( int cuenta = 0; cuenta < nombres.length; cuenta++ ) {
28          botones[ cuenta ] = new JButton( nombres[ cuenta ] );
29          botones[ cuenta ].addActionListener( this );
30          botones[ cuenta ].setToolTipText("Borra del contenedor al boton "+nombres[cuenta]);
31       }
32 
33       // colocar botones en BorderLayout; no importa el orden
34       contenedor.add( botones[ 0 ], BorderLayout.NORTH ); 
35       contenedor.add( botones[ 1 ], BorderLayout.SOUTH ); 
36       contenedor.add( botones[ 2 ], BorderLayout.EAST );  
37       contenedor.add( botones[ 3 ], BorderLayout.WEST );  
38       contenedor.add( botones[ 4 ], BorderLayout.CENTER ); 
39 
40       setSize( 350, 200 );
41       setVisible( true );
42 
43    } // fin del constructor de DemoBorderLayout
44 
45    // manejar eventos de botón
46    public void actionPerformed( ActionEvent evento )
47    {
48       for ( int cuenta = 0; cuenta < botones.length; cuenta++ )
49 
50          if ( evento.getSource() == botones[ cuenta ] )
51             botones[ cuenta ].setVisible( false );
52          else
53             botones[ cuenta ].setVisible( true );
54 
55       // re-esquematizar el panel de contenido
56       esquema.layoutContainer( getContentPane() );
57    }
58 
59    public static void main( String args[] )
60    { 
61       DemoBorderLayout aplicacion = new DemoBorderLayout();
62       aplicacion.setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );
63    }
64 
65 } // fin de la clase DemoBorderLayout
