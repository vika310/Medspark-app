// Medspark Mobile App (React Native + Tailwind via NativeWind)

import React from "react"; import { NavigationContainer } from "@react-navigation/native"; import { createNativeStackNavigator } from "@react-navigation/native-stack"; import { View, Text, TouchableOpacity, ScrollView } from "react-native"; import { styled } from "nativewind";

const Stack = createNativeStackNavigator(); const StyledView = styled(View); const StyledText = styled(Text); const StyledTouchable = styled(TouchableOpacity);

const features = [ { name: "Practice Questions", screen: "Practice" }, { name: "Mock Tests", screen: "MockTests" }, { name: "Notes & Formulas", screen: "Notes" }, { name: "NCERT Solutions", screen: "NCERT" }, { name: "Diagrams", screen: "Diagrams" }, { name: "Flashcards", screen: "Flashcards" }, { name: "Study Timer", screen: "Timer" }, { name: "Progress Tracker", screen: "Progress" }, { name: "Doubt Support", screen: "Doubts" }, { name: "Leaderboard", screen: "Leaderboard" }, ];

function HomeScreen({ navigation }) { return ( <StyledView className="flex-1 bg-purple-100 p-4"> <StyledText className="text-3xl font-bold text-purple-800 text-center mb-4">Medspark</StyledText> <ScrollView> {features.map((feature, index) => ( <StyledTouchable key={index} onPress={() => navigation.navigate(feature.screen)} className="bg-white p-4 rounded-xl shadow my-2" > <StyledText className="text-purple-700 font-medium text-lg text-center"> {feature.name} </StyledText> </StyledTouchable> ))} <StyledTouchable onPress={() => navigation.navigate("Login")} className="bg-purple-600 mt-6 py-3 rounded-xl" > <StyledText className="text-white text-center font-semibold">Login / Signup</StyledText> </StyledTouchable> </ScrollView> </StyledView> ); }

function PlaceholderScreen({ route }) { return ( <StyledView className="flex-1 justify-center items-center bg-purple-50"> <StyledText className="text-xl text-purple-700 font-semibold"> {route.name} Screen Coming Soon! </StyledText> </StyledView> ); }

function LoginScreen() { return ( <StyledView className="flex-1 justify-center items-center bg-white p-6"> <StyledText className="text-2xl text-purple-800 font-semibold mb-4">Login Page</StyledText> {/* Add TextInputs & Login Logic Here */} </StyledView> ); }

export default function App() { return ( <NavigationContainer> <Stack.Navigator> <Stack.Screen name="Home" component={HomeScreen} /> <Stack.Screen name="Login" component={LoginScreen} /> {features.map((feature, index) => ( <Stack.Screen key={index} name={feature.screen} component={PlaceholderScreen} /> ))} </Stack.Navigator> </NavigationContainer> ); }

